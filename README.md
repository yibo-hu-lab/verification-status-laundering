# Silence Is Endorsement
### Verification-Status Laundering in LLM Agent Pipelines

Yibo Hu · Illinois Institute of Technology

📄 Paper: *arXiv link forthcoming*

## Key finding

Safety monitors in LLM agent systems usually judge an action from a summary or a stored
handoff, not from the original evidence. A lossy handoff can keep the claim that an action is
*authorized* while dropping the fact that the claim was never verified. We call this
**verification-status laundering**: the authorization claim survives, but the verification
status needed to interpret it is weakened, detached, or lost, so a bare "authorized" reads as
settled.

Across nine open-weight monitors and two hosted models, holding the action and authorization
claim fixed and removing only the unverified provenance framing:

- Risky approval rises from **5% to 60%** on Llama-3.1-8B and **9% to 98%** on Qwen2.5-14B;
  every open-weight monitor's 95% bootstrap interval for the effect excludes zero except the
  two whose approval is already at ceiling.
- Ordinary components create the degraded handoff with no adversary: summarizers weaken the
  status (**0.10–0.13** lost outright), memory compressors often remove it (**0.36–0.90**),
  and a full proposer → summarizer → memory → monitor pipeline raises risky approval to
  **57–81%**.
- On independently authored harmful and unsafe items (WildGuard, ATBench), an unsupported
  authorization claim also raises approval.
- Instructing the monitor to distrust unverified authorization is **not a reliable cross-model
  fix**: some models follow the distinction, others over-refuse legitimate requests, and others
  remain exposed.

The design implication is that agent systems should carry verification status as structured
state bound to the claim, and check that it survives every handoff, rather than trusting that
the words in a rewritten note still carry it.

> The claim survives the handoff; the fact that it was never verified does not.

## Code and data

The reproduction package — the controlled-probe stimuli and four-condition protocol, the
two-annotator summarizer and memory channel audit, the composed-pipeline runs, the
marker-wording, placement, and policy-instruction controls, and the figure scripts — **will be
released here upon publication. In the meantime, it is available from the author on request.**

## Citation

```bibtex
@article{hu2026silence,
  title  = {Silence Is Endorsement: Verification-Status Laundering in LLM Agent Pipelines},
  author = {Hu, Yibo},
  year   = {2026},
  note   = {arXiv preprint forthcoming}
}
```
