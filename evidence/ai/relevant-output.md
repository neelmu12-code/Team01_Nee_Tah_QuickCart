# Relevant AI output from the supplied screenshots

The [original PNG screenshots are included here](screenshots/README.md), grouped by their prompts. The text below transcribes selected **visible excerpts**, not a reconstruction of the full responses. Section numbers jump because intermediate content was not supplied. Ellipses in attachment labels and cropped screenshot boundaries are not evidence of any particular missing text. Original conversation date/model and any downloadable ZIP contents are not established by the screenshots.

## Response to P1: requirements analysis

> I've gone through all 7 pages of the QuickCart project instructions. The biggest thing to understand is that we are not being asked to build an application or simply write a bunch of JUnit tests. We're being asked to evaluate how trustworthy an existing application is, using evidence from multiple testing techniques.

The visible project-overview table states:

| Field | Visible output |
| --- | --- |
| Course weight | 20% |
| Final deadline | Dec 2, 2026; 10:00 PM |
| Group size | 2 students |
| Recorded demonstration | ~5 minutes |

> That means the project has three big goals:
>
> 1. Design good tests that verify the requirements and uncover potential defects.
> 2. Measure how effective those tests are using coverage, mutation testing, and other techniques.
> 3. Defend our conclusions with actual evidence rather than just claiming the application works.

> One important rule: we generally should not fix the production code. We're evaluating it, not repairing it.
> The instructions also explicitly say to treat this as independent of Assignment 1.

The visible concepts table lists:

| Concept / tool | What it does | Requirement |
| --- | --- | --- |
| Equivalence partitioning | Groups inputs with similar expected behaviour | Required |
| Boundary-value testing | Tests inputs around important limits | Required |
| JUnit 5 | Runs automated functional tests | Required |
| Parameterized testing | Runs tests across different input values | Where appropriate |
| Test doubles / mocking | Replaces a real dependency during testing | At least one meaningful use |
| Integration testing | Tests real components working together | At least one meaningful test |
| JaCoCo | Measures which code is executed | Required |
| PIT mutation testing | Measures whether tests detect small code changes | Required |
| jqwik | Generates inputs to verify general properties | At least one meaningful property |
| AI-assisted testing | Evaluates AI-generated tests against human testing | Required experiment |

### Visible section 13: How I would approach the project

> We have approximately three weeks until December 2. I would organize the work into the following stages.

1. **Understand the QuickCart specification and source code.** Visible explanation: identify classes, requirements, inputs, outputs, and high-risk business logic; decide which tests provide the strongest evidence.
2. **Design and implement JUnit 5 tests.** Visible explanation: use partitions/boundaries, negative cases, parameterized tests, meaningful integration testing, and a justified test double.
3. **Run JaCoCo and PIT.** Visible explanation: establish initial results, investigate missing branches/survivors, improve tests, and capture before-and-after evidence.
4. **Implement jqwik and evaluate AI-generated tests.** Visible explanation: implement a meaningful generated-input property and run a controlled AI experiment with saved prompts, outputs, and comparative results.
5. **Compile evidence and record the demonstration.** Visible explanation: document two defects, assess residual risk, prepare the Evidence Sheet, verify the repository runs, and rehearse the video.

The numbered explanations above are summaries of the visible text, not verbatim quotations.

> The instructions don't require a particular number of test cases, a specific coverage percentage, or a perfect mutation score. This is important because our time should go toward high-value tests with clear reasoning, not simply generating hundreds of assertions.

## Response to P2: proposed skeleton

The visible Explorer diagram proposes this layout (indentation transcribed; descriptive arrows are retained):

```text
Team##_XXX_YYY_QuickCart/
  .vscode/
    extensions.json
    settings.json
  src/
    main/
      java/  <- supplied QuickCart source
      resources/
    test/
      java/
        PricingTest.java
        CouponTest.java
        OrderIntegrationTest.java
        PaymentMockTest.java
        CartPropertyTest.java
      resources/
  evidence/
    coverage/
    mutation/
    ai/
      prompts.md
      relevant-output.md
    strategy.md
    defects.md
    project-evidence-sheet.md
    demo-outline.md
  pom.xml
  README.md
  .gitignore
```

> This follows the required repository structure on page 4 of your instructions, with additional organisational files to make our work easier.

The visible status checklist marks VS Code structure, Maven configuration, JUnit/Mockito starter templates, JaCoCo/PIT configuration, and evidence/video templates as prepared. It marks actual QuickCart source, specification-based tests, and real coverage/mutation/defect evidence as still needed. These are the historical AI response's claims; the screenshots alone do not verify the contents of an archive or any generated files.

> I deliberately left the JUnit templates disabled and the jqwik property unimplemented, rather than inventing QuickCart classes or tests that appear to pass without testing anything. I've checked the ZIP and XML structure, but I haven't run a Maven build of the project.

> The next thing I need is the actual QuickCart source code and behavioural specification provided by your professor. With those, we can transform this from a starter skeleton into a real functioning test project, working through every class and required testing concept together.

## Scope of the P1/P2 evidence

The supplied output helps explain planning and the proposed structure. It contains no visible executable test bodies, test-run results, or mutation results. The named starter test files do not match every final test filename, and the diagrams' optional Evidence Sheet/video templates are not claimed to exist. These excerpts therefore support disclosure of AI use, while the separately recorded [test-generation experiment](candidate-output.md) supplies executable candidate output and [evaluation](evaluation.md).

## Response to P4: supplementary requirements outline

Added November 27, 2026. The [existing outline prompt](screenshots/09-prompt-outline-requirements.png) has been reused. The response is preserved in [the first requirements image](screenshots/10-output-outline-requirements.png), [its continuation](screenshots/11-output-outline-requirements-continued.png), and [the deliverables image](screenshots/12-output-outline-deliverables.png).

The visible output restates the assignment purpose: test the supplied Java ordering system and explain the confidence justified by the results. Its table lists risk-based strategy, specification-based JUnit tests, meaningful test doubles and integration, JaCoCo interpretation, PIT survivor investigation and improvements, jqwik properties, critical AI evaluation, two significant defects, and overall quality/residual risk. It emphasizes that no numerical test-count, coverage, or mutation-score target is required.

The deliverables section describes the required repository layout, a maximum two-page Evidence Sheet, and the narrated demonstration. It gives a five-minute target, a 4:30-5:30 penalty-free window, readable evidence, and roughly equal technical participation. These are summaries of the visible AI output; the assignment document remains authoritative. The screenshots repeat planning topics already covered by P1 but preserve a different visible prompt and response, so they are grouped as supplementary evidence rather than a new testing experiment.

## Response to P5: risk-based testing

Added November 27, 2026. Primary images: [risk-prioritization output](screenshots/14-output-risk-priorities.png) and [reported results and limitations](screenshots/15-output-risk-results-limitations.png). The quoted statements and table below are the AI response's claims, not newly measured repository results.

> Payment and inventory consistency is QuickCart's highest risk. With 3 units in stock and 2 requested, a declined payment left only 1 unit available. QuickCart then rejected the identical retry as `OUT_OF_STOCK` before the gateway could approve it.

> I ranked risks by impact × exposure to checkout paths and ran nine scenarios with real pricing, order, and inventory services and a fake payment gateway.

The four visible ranked rows state:

| Priority | Risk | Reported score | What the response says the test showed |
| --- | --- | ---: | --- |
| 1 | Stock changes before payment approval | 16 | A decline blocked a valid retry; a gateway exception also reduced stock from 5 to 3. |
| 2 | Gateway authorizes the wrong total | 12 | A discounted Ontario order with paid shipping sent $114.08 to the gateway, compared with a stated correct total of $115.25. |
| 3 | Two lines for one SKU exceed shared stock | 8 | Requesting 2 + 2 units with 3 available threw an exception after reducing stock to 1. |
| 4 | Checkout rejects exact stock | 6 | Requesting 2 units with exactly 2 available returned `OUT_OF_STOCK`; an existing regression already covered the boundary. |

The table transcribes the meaning and visible figures; it is not a complete list of the nine reported probes. The screenshots do not define the scoring scales.

The visible closing paragraphs state:

> Four of nine probes passed. Five exposed specification failures. I added six JUnit 5 cases covering the decline and retry, gateway exception, authorization amount, and repeated-SKU orders with 3, 4, or 5 units available. The repeated-SKU cases treat matching product IDs as demand on one shared stock balance. Basic model checks received lower priority.

> The archive includes the strategy, test cases, and observed results. Validation ran directly in Java. Maven was unavailable here, so the full JUnit suite, JaCoCo, and PIT were not rerun.

The displayed archive link is named `QuickCart_Risk_Based_Testing.zip`. The archive, probe implementation, raw results, and six proposed JUnit bodies were not supplied with these screenshots and were not found in the reviewed project. Their contents and execution cannot be verified from the images. This additional output is retained for critical evaluation without importing unprovided tests or changing the verified coverage/mutation figures.

## Response to P6: historical code/evidence audit

Screenshots received November 27, 2026, documenting the November 11 audit in this project conversation: [request and activity](screenshots/16-prompt-audit-and-activity.png), [testing checklist](screenshots/17-output-audit-testing-checklist.png), and [remaining checklist](screenshots/18-output-audit-gaps-checklist.png). These excerpts concern the repository at the time of the audit, before the later documentation, AI-evidence, and layout updates.

The visible activity says the coverage/mutation figures match the saved raw results: 100% coverage and 27 of 31 mutants killed. It also points out that specification violations coexist with those scores and reports that both AI evidence files were empty at that time. Another intermediate update says a temporary-copy build stopped at a file-access error before tests ran; that update is not the outcome of every later verification run.

The visible audit checklist reports:

| Requirement | Historical assessment shown in the screenshots |
| --- | --- |
| JUnit functional tests | Present: exact monetary assertions, boundaries, valid/invalid inputs and parameterized cases. |
| Meaningful test doubles | Present: payment amounts, reservations, absent interactions and interaction order checked with Mockito. |
| Integration testing | Present: real pricing/inventory components interact with a fake payment dependency. |
| Property-based testing | Present: four jqwik properties and 800 generated checks. |
| JaCoCo coverage and interpretation | Present and internally consistent. |
| PIT mutation analysis and improvements | Present and internally consistent. |
| Concise testing strategy | Partial: rationale was scattered rather than clearly summarized. |
| Controlled AI experiment | Incomplete: tests/control profile existed, but saved prompts, output, evaluation and comparisons were missing. |
| Two significant defect reports | Partial: reproduction evidence existed, but a selected pair with impact/severity still needed presenting. |
| Overall quality/residual-risk assessment | Present in coverage/mutation discussions, with final-deliverable presentation still needed. |
| Evidence Sheet | Not found in the reviewed project. |
| Recorded demonstration | Not found there; a recording stored elsewhere could not be verified. |
| Required submission hierarchy | Did not match the assignment PDF at that point. |

The table summarizes visible text; overlapping rows from the two checklist screenshots are listed once. The audit identified useful completion work and appropriately distinguished structural coverage from correctness. It did not provide a new test-generation experiment in these excerpts.

**Historical context:** the AI prompt/output/evaluation files, concise strategy and defect notes, and root-level source layout were added or completed afterward. Their current evidence is linked from [README.md](../../README.md). The team's Evidence Sheet and video remain separately planned deliverables. The screenshot's old missing-item statements do not replace the current evidence, and its figures do not change the recorded P3 control/treatment measurements.
