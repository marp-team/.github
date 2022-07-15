# Contributing to Marp projects

Thank you for taking the time to read how to contribute to our project! This is the basic guideline for contributing to [Marp team owned projects][marp-team].

You can start contributing our project in several ways: improve docs, report bug, request feature, writing code, and so on.

Depending on the project you want to contribute, it might have additional guidelines you should follow at that repository. Please also check the guideline per repository.

> :information_source: Would you the first time to contribute OSS? [Open Source Guides](https://opensource.guide/how-to-contribute/) might help you.

## [Code of conduct][code-of-conduct]

We follow [Contributor Covenant Code of Conduct][code-of-conduct] in the all of repositories managed by [Marp team][marp-team].

## Architecture

[<img align="left" src="architecture.svg" width="25%" />](architecture.svg)

A figure on the left shows the whole of architecture in the Marp ecosystem. Yellow arrows are meaning dependency.

**[Marpit]** is the center of the ecosystem and the independent framework for developers. It's designed suitable for not only Marp but also other slide libraries (See examples of collaboration with [reveal.js](https://codesandbox.io/nw80vrxvpp) and [WebSlides](https://codesandbox.io/j3wo2091yw)).

You are probably using **[Marp Core]** if you are creating a slide deck with Marp. It includes built-in themes, settings that suit for Marp tools, and Markdown extensions that break CommonMark.

And the most of Marp apps (CLI, Web, Desktop...) and integrations (VS Code, React, Vue...) are creating based on [Marp Core]. [Marp CLI](https://github.com/marp-team/marp-cli) is a precious exception that supports Marpit-based converter for power users.<br clear="all" />

[marpit]: https://github.com/marp-team/marpit
[marp core]: https://github.com/marp-team/marp-core

## [Question]

Please see [`SUPPORT.md`][question] if you would like to ask any question.

We have [GitHub Discussions] to engage with other Marp community members.

[github discussions]: https://github.com/marp-team/marp/discussions

## Report issue

Do you have a feedback that is not just a question? We're welcome to report it into Marp owned project.

At first, you should search for similar issues before reporting your issue. It may have already been discussed or resolved in the other issue.

[:mag: `org:marp-team is:issue [keyword]`](https://github.com/search?q=org%3Amarp-team+is%3Aissue+%5Bkeyword%5D) is useful to search issue from across our projects.

If you could not find out a similar issue, you can create a new issue. Please not contain multiple reports into one issue. It should have only one theme.

> :information_source: Some projects have consisted of [Marp team][marp-team] owned packages based on [project architecture](#architecture). If you know which project causes an issue, please report the issue to that repository. The member of Marp team may [transfer the reported issue](https://help.github.com/en/articles/transferring-an-issue-to-another-repository) into the proper repository.

### Feature request

Feature request is welcome because it could give feedback to us.

However, we have to take a moment to judge whether fitting to the project aim and scope. We require clear benefit and strong incentive to work for the request because each our projects should keep simple and smart.

We recommend to post about your request into [GitHub Discussions][github discussions] at first. Talk about your new idea with Marp community.

### Bug report

> :warning: Did you find a security vulnerability? _Report directly to security@marp.app instead of opening a new issue._

We highly recommend to use "🐛 Report a bug" issue form in the corresponding repository to the bug. To assist in finding the bug by contributor rapidly, it is good to describe these:

- Expected behavior and actual behavior
- Necessary steps and resources to reproduce bug
- Occurred environment (e.g. the version of OS, browser, Node.js, and so on)

## Pull request

You can submit pull request if you have fixed or added useful something to our projects.

### Before adding new feature

_Marp team is not proactive for enhanceing our syntax_, because the custom Markdown flavor may make user's confusions and protests whose are familiar with exist Markdown/CommonMark syntax.

We are always suggesting **"Use or create the third-party [plugin](https://marpit.marp.app/usage?id=extend-marpit-by-plugins) if you want"** rather than adding new syntax. For implementing new syntax and new feature to offical tools, we require able to confirm a worth through a created third-party plugin and many real-world presentations using it. We will consider integrating the plugin as built-in feature if the most of Marp community shows that using the plugin is valuable.

### [Good first issues](https://github.com/search?q=org%3Amarp-team+is%3Aopen+label%3A%22good+first+issue%22)

Some of issues have been labeled [**`good first issue`**](https://github.com/search?q=org%3Amarp-team+is%3Aopen+label%3A%22good+first+issue%22) to indicate the issue to suit to new contributors. We're always welcome to send the pull request about them.

- **Low barrier to contribute**: It is expected to be resolved the issue with simple modification, without advanced knowledgements about the architecture of Marp ecosystem.

- **The clear context/solution**: In many cases, the clear context and solution (or one of them) has been already mentioned in the labled issue.

- **Nice to have**: Generally the labled issues are not in pressing needs, but would make definetely better for users.

Working on `good first issue` would becomes the good first step for contributing to Marp projects via coding. It's also helpful for learning the basic architecture about a contributing project.

> **Note**
> This label does not mean to restrict a contributor by the number of contribution times to the project. Everyone can contribute if you thought it is worth to resolve.

### Requirements in pull request

- **Indicate related issue(s) in description of PR.** In many cases, the created PR should already have related problems. GitHub can [close issue automatically by keyword](https://help.github.com/articles/closing-issues-using-keywords/).

- **Keep code styling.** We are using [yarn] package manager, [Prettier] formatter, and linters for each language. CI build would fail when using the wrong format/style. It could fix by `yarn format --write` and `yarn lint:[lang] --fix` in most projects.

- **Maintain tests.** We need to fill code coverage by writing meaningful tests. In many projects, we are setting a threshold of global line coverage to 95%. You could measure coverage in local by running `yarn test:coverage`.

### For maintainer

These are tasks for maintainer, and usually committer doesn't have to worry.

- If there is CHANGELOG.md in a working project, the maintainer has to update it after (or while) merge PR. We're adopting the format based on [Keep a Changelog].

## Release

The core maintainer can release package or product of marp-team projects.

> :warning: You have to use `npm` in a release process, and NEVER use `yarn`.

### Versioning

Basically we are following [Semantic Versioning].

#### Pre-release

We treat `v0.0.x` as the pre-release version. It may update only patch version until reach to the stable implementation even if it has some breakings or incompatible changes.

Maintainer should mark `v0.0.x` as "Pre-release" in GitHub release page.

#### Bump version

We have automated bumping version with [`version` npm script](https://github.com/marp-team/actions#npm-version-helper-script) in many repositories.

If it is defined in `package.json`, run `npm version [major|minor|patch]` at latest `master` branch to bump version. In many cases, it would add the version tag and update CHANGELOG.md through helper script.

After than, push master branch and tag by `git push && git push --tags`. [GitHub Actions for Marp team](https://github.com/marp-team/actions) can be automate to publish GitHub Releases generated from updated CHANGELOG.md whenever pushing new tag .

### Publish to npm

Several repository provide [npm package](https://www.npmjs.com/org/marp-team). The core maintainer can publish package to npm after bumping version.

```
npm publish
```

For the security reason, we are not planned to automate publishing. [We require two-factor authentication to publish](https://blog.npmjs.org/post/175861857230/two-factor-authentication-protection-for-packages).

> :information_source: Maintainer should configure to check code styling and tests again when running important commands through `preversion` (bumping version) and `prepack` (publish to npm).

[code-of-conduct]: ./CODE_OF_CONDUCT.md
[question]: ./SUPPORT.md#question
[marp-team]: https://github.com/marp-team/
[yarn]: https://yarnpkg.com/
[prettier]: https://prettier.io/
[keep a changelog]: https://keepachangelog.com/en/1.0.0/
[semantic versioning]: https://semver.org/
