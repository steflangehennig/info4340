---
layout: page
title: "Week 0: Before the first class"
permalink: /schedule/week-0/
---

<div class="note" markdown="0">
  <strong>Do this before Week 1's first lecture.</strong> &nbsp;|&nbsp;
  <strong>Time:</strong> about 90 minutes &nbsp;|&nbsp;
  <strong>Credit:</strong> counts toward participation &nbsp;|&nbsp;
  <strong>Submit:</strong> setup check output + survey via Canvas
</div>

## Why this week exists

This is a 10-week quarter. If we spend the first two class sessions troubleshooting installs, we lose a meaningful chunk of the course. Week 0 moves that work to a time when it costs you an evening instead of costing all of us class time.

None of this requires prior Python experience, and none of it requires you to spend money. If something breaks, that is expected and fine - submit the output anyway and say what you tried. 

## The checklist

| # | Task | Time | Required? |
|---|---|---|---|
| 1 | Confirm your accounts (Canvas, Google, GitHub) | 15 min | Yes |
| 2 | Install Python, VS Code, and Git | 30 min | Yes |
| 3 | Install the course Python packages | 10 min | Yes |
| 4 | Run the setup check and submit the output | 10 min | Yes |
| 5 | Complete the pre-course survey | 10 min | Yes |
| 6 | Bring two stories to Monday | 15 min | Yes |
| 7 | Install the AI coding CLIs | 20 min | Optional - we do this in Week 2 |

---

## 1 &nbsp;Confirm your accounts

<div class="session-block" markdown="0">
  <div class="session-label">Accounts</div>
  <div class="session-content">
    <div class="session-title">Three logins you need working before Monday</div>
    <ul style="font-size:14px; color:var(--muted); line-height:1.7; margin:0 0 0 18px;">
      <li><strong>Canvas</strong> - confirm INFO 4340 appears in your course list and you can open the Week 0 assignment.</li>
      <li><strong>Google account</strong> - open <a href="https://colab.research.google.com" target="_blank">Google Colab</a> and confirm you can create a new notebook. Colab is our fallback if a local install fights you and some in-class work runs there.</li>
      <li><strong>GitHub</strong> - create a free account at <a href="https://github.com/signup" target="_blank">github.com/signup</a> if you do not have one. Use an email you will keep after graduation. You will version your project work here starting in Week 3.</li>
    </ul>
  </div>
</div>

<div class="note" markdown="0">
  <strong>While you are there:</strong> apply for the <a href="https://education.github.com/discount_requests/application" target="_blank">GitHub Student Developer Pack</a> with your DU email. It is free, takes two minutes, and approval can take a few days, so start it now rather than in Week 3.
</div>

## 2 &nbsp;Install Python, VS Code, and Git

Work through **sections 1, 2, and 6** of the [developer setup guide]({{ site.baseurl }}/guides/dev-setup/). It has separate Mac and Windows paths (use the OS toggle at the top of that page).

You need three things installed:

- **Python 3.10 or newer** - download from [python.org/downloads](https://www.python.org/downloads/). On Windows, **check "Add Python to PATH"** on the first installer screen. This one checkbox causes most of the setup problems in this course.
- **VS Code** plus the Microsoft **Python extension** - this is where you will write and run code.
- **Git** - [git-scm.com/downloads](https://git-scm.com/downloads). Then set your name and email as shown in section 6 of the setup guide.

Windows users: the setup guide asks you to install WSL2. That step is only needed for the AI coding CLIs in Week 2. You can skip it now if it gives you trouble.

## 3 &nbsp;Install the course packages

Open a terminal - in VS Code, press `` Ctrl+` `` (backtick) - and run:

```
pip install pandas numpy matplotlib scikit-learn statsmodels anthropic requests networkx jupyter
```

If `pip` is not recognized, try `pip3` or `python -m pip install ...` instead. On Mac you may need `python3 -m pip`.

This takes a few minutes and prints a lot of text. That is normal. You are looking for `Successfully installed` near the end.

## 4 &nbsp;Run the setup check

This is the part you will actually submit. Copy the script below into a file called `setup_check.py`, save it somewhere you can find, then run `python setup_check.py` from a terminal in that folder.

The script is also posted on Canvas if you would rather download it.

```python
"""INFO 4340 Week 0 setup check. Run: python setup_check.py"""
import importlib, os, platform, shutil, sys

MIN_PYTHON = (3, 10)
PACKAGES = [
    ("pandas", "pandas", True), ("numpy", "numpy", True),
    ("matplotlib", "matplotlib", True), ("sklearn", "scikit-learn", True),
    ("statsmodels", "statsmodels", True), ("anthropic", "anthropic", True),
    ("requests", "requests", True), ("networkx", "networkx", False),
    ("jupyter", "jupyter", False),
]
COMMANDS = [
    ("git", "Git", True), ("code", "VS Code CLI", False),
    ("claude", "Claude Code CLI", False), ("codex", "Codex CLI", False),
]
results = []

def record(ok, required, label, detail=""):
    results.append(("PASS" if ok else ("FAIL" if required else "SKIP"), label, detail))

print("=" * 68)
print("INFO 4340 SETUP CHECK")
print("=" * 68)
print(f"Operating system : {platform.system()} {platform.release()}")
print(f"Python executable: {sys.executable}\n")

v = sys.version_info
record((v.major, v.minor) >= MIN_PYTHON, True, "Python version",
       f"{v.major}.{v.minor}.{v.micro}")

for module_name, friendly, required in PACKAGES:
    try:
        mod = importlib.import_module(module_name)
    except ImportError:
        record(False, required, friendly, "not installed")
    except Exception as exc:
        record(False, required, friendly, f"import error: {type(exc).__name__}")
    else:
        record(True, required, friendly, getattr(mod, "__version__", "installed"))

for command, friendly, required in COMMANDS:
    path = shutil.which(command)
    record(bool(path), required, friendly, path or "not on PATH")

key = os.environ.get("ANTHROPIC_API_KEY", "")
record(bool(key), False, "ANTHROPIC_API_KEY",
       f"set ({len(key)} chars)" if key else "not set - you get the class key in Week 1")

try:
    with open("_write_test.tmp", "w") as f:
        f.write("ok")
    os.remove("_write_test.tmp")
    record(True, True, "Write files to disk", "working directory is writable")
except Exception as exc:
    record(False, True, "Write files to disk", f"{type(exc).__name__}: {exc}")

print("-" * 68)
print(f"{'STATUS':<8}{'CHECK':<24}DETAIL")
print("-" * 68)
for status, label, detail in results:
    print(f"{status:<8}{label:<24}{detail}")
print("-" * 68)

n_fail = sum(1 for s, _, _ in results if s == "FAIL")
n_skip = sum(1 for s, _, _ in results if s == "SKIP")
print(f"{sum(1 for s, _, _ in results if s == 'PASS')} passed | "
      f"{n_fail} failed | {n_skip} optional not installed\n")

if n_fail == 0:
    print("Ready to roll. Paste this entire output into Canvas.")
else:
    print("Not ready yet. Fix the FAIL rows, then run this again.")
    print("Most common fix:")
    print("  pip install pandas numpy matplotlib scikit-learn statsmodels "
          "anthropic requests networkx jupyter")
    print("\nStuck for more than 20 minutes? Submit this output anyway and post")
    print("it in the Week 0 discussion thread. We will fix it together.")
print("=" * 68)
```

<div class="note" markdown="0">
  <strong>What to submit:</strong> the entire output, from the first <code>====</code> line to the last, pasted as text into the Canvas Week 0 assignment. Not a screenshot - text, so I can search it. A result with <code>FAIL</code> rows still earns full credit as long as you say what you tried.
</div>

Optional rows marked `SKIP` are fine. You are aiming for **zero `FAIL` rows**.

## 5 &nbsp;Pre-course survey

Ten minutes, on Canvas. It asks about your Python background, which AI tools you already use, what you want out of the course, and what industry you are heading into/already in. I use it to form project groups and to calibrate how fast we move through the technical material, so please answer honestly rather than aspirationally.

## 6 &nbsp;Bring two stories to Monday

No readings this week. Instead, come to the first session with two specific examples:

1. **A time GenAI genuinely helped you** - what you asked for, what it gave you, why it worked.
2. **A time it failed, misled you, or surprised you** - what went wrong, and how you noticed.

"How you noticed" is the interesting part and it's what the course is built around. If you have never used these tools, spend fifteen minutes with one this week and ask it something you already know the answer to. Watch what it gets wrong.

## 7 &nbsp;Optional: the AI coding CLIs

Sections 3, 4, and 5 of the [developer setup guide]({{ site.baseurl }}/guides/dev-setup/) cover installing **Claude Code** and **Codex CLI**. These require an account or API key, so we set them up properly in Week 2 once you have the class API key.

If you already have a Claude or ChatGPT subscription and want a head start, install them now because the setup check will pick them up. If not, skip this section. **You will not fall behind.**

## What you do not need

- **You do not need to buy anything.** A class API key covers all coursework. If any Week 0 step asks for a credit card, don't give it to them.
- **You do not need prior Python.** This is not a programming class. Week 1 assumes zero.
- **You do not need your own API key.** You get the class key in Week 1.
- **You do not need Anaconda.** Plain Python from python.org is what these instructions assume. If you already run Anaconda, that is fine too - use `conda install` instead of `pip install` in step 3.

## If you get stuck

Give it a genuine 20 minutes, then stop. Post in the **Week 0 discussion thread on Canvas** with:

- your operating system
- the exact command you ran
- the complete error message, copied as text

I check that thread daily the week before class, and setup problems are almost always quick fixes once someone else looks at them. Anything unresolved by Monday we handle in the first class.

