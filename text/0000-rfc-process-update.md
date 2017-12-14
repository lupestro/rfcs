---
tags: ember, ember-cli
---

- Start Date: (fill me in with today's date, YYYY-MM-DD)
- RFC PR: (leave this empty)
- Ember Issue: (leave this empty)

# RFC Process Update

## Summary

Introduce the idea of Core Champion to the Ember.js RFC process, merge Ember.js and Ember CLI RFCs repositories,
and add metadata to make cross-project RFCs easier.

## Motivation

Inspired by Rust, Ember implemented a Request For Commits (RFC) process with the intent to involve the community in discussing the future of the framework.
The RFC process has proved invaluable, proposals by both Core and community members are discussed and refined,
with the result coming out much stronger.
Other projects like React also adopted an RFC process, lending external validation to this idea.

After having been involved with the RFC process for some time, and from feedback from the community, some issues with the current implementation of the process have been noted.

### Confusion about emberjs/rfcs and ember-cli/rfcs

The Ember project currently has two separate RFC processes for Ember.js and Ember CLI.

This leads to confusion due to having to keep track of two different repositories to track progress.
It also increases the burden on the submitter of an RFC, as the two processes have diverged slightly,
making the submitter be aware of these differences during the lifecycle of the RFC.

There are also some cases where it is not clear exactly which repository the RFC should be submitted to.
This can also lead to multiple RFCs being written, one for each repository.
While multiple RFCs might be warranted in some cases,
it should be a choice instead of a limitation of the current processes.

### Process does not cover sufficient areas of development

RFCs to emberjs/rfcs and ember-cli/rfcs concern themselves mostly with features or deprecations to ember.js and ember-cli respectfully, with some ember-data proposals in emberjs/rfcs.

Once again taking inspiration from Rust, they have experimented expanding the types of RFCs proposed
[crates.io default ranking](https://github.com/rust-lang/rfcs/blob/master/text/1824-crates.io-default-ranking.md)
[default URLs for documentation](https://github.com/rust-lang/rfcs/blob/master/text/1826-change-doc-default-urls.md).
The latter one, for example, would have been a useful RFC when designing the new [API docs](https://github.com/ember-learn/ember-api-docs).

Rust has RFCs for documentation, website, internals, tools.
We only have emberjs and ember-cli due to them having been implemented separately.

This makes it so that a potential contributor does not know where to submit a proposal.

### Lingering RFCs

The emberjs/rfcs repository currently has [54 issues](https://github.com/emberjs/rfcs/issues) and [62 PRs](https://github.com/emberjs/rfcs/pulls) open.
Of these, only a relatively small percentage has been active in the recent past.

We have kept PRs and issues open so people could more easily find the discussions, but this has instead given a negative feeling of staleness,
as RFCs linger open without new feedback.

## Detailed design

To address the issues raised in the “Motivation” section, I will propose changes to the current process.

### Implement Core Champion

To make sure that RFCs receive adequate support from the team, Ember CLI has implemented the idea of a champion associated with each RFC.
The goal is that in seeking a champion from the team, the RFC author starts a dialogue with the team and gets some early feedback. The champion is then responsible for representing the RFC in team meetings, and for shepherding its progress.

This will be imported into emberjs/rfcs.

### Improve the lifecycle of RFCs

Learning from Rust once again, have a Final Comment Period (FCP) to close.
- FCP to close
  - Major redesign that would benefit from a fresh conversation
  - Inactivity from author
  - Misalignment with Ember philosophy

### Open process to more types of RFCs

- Should be focused on teams, not projects, as it is a certain team that is responsible for a certain project.
  - Add front matter to existing RFCs
  - Add README prose that RFCs can be moved to FCP and accepted by the respective teams involved
- Design work template (?)
- Content template (?)

### Unify ember-cli/rfcs and emberjs/rfcs

- Remove active/completed concepts from ember-cli/rfcs
  - Copy both active and completed RFC files into `text` of emberjs/rfcs
  - Add front matter

## How We Teach This

- Improved README
  - Lifecycle graph
  - Description of the process once RFC is finished
- New Contributors page on website with prose related to this
- Statusboard page improvements ?

## Drawbacks

### Adjustment period

There are active RFCs in ember-cli/rfcs. Moving these discussions would be onerous, so they should be kept there until completion, and no new RFCs accepted.

### Permalinks to ember-cli/rfcs proposals

Moving the RFC files from ember-cli/rfcs (active or completed) to emberjs/rfcs can be seen as a breaking change, and could lead to someone linking to ember-cli/rfcs and then the RFC being updated in emberjs/rfcs. However, ember-cli/rfcs already suffers from a linking problem due to the active/completed folders, as RFCs need to be moved from one to the other even after being accepted.
This could be mitigated by introducing a warning in the RFC text directing people to the new source.

## Alternatives

None at the moment.

## Unresolved questions

None at the moment.

----------

## Glossary

- **RFC**: Request For Comments. The process by which a proposal is discussed by the community and then approved by an Ember team.
- **FCP**: Final Comment Period. Period of one week at the end of which an RFC is to be accepted or rejected by an Ember team. Extended in periods of one week if new concerns are raised.
