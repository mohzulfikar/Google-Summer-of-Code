<div align="center">
    <a href="https://summerofcode.withgoogle.com/programs/2022/projects/00w1CCXe"><img src="image/gsoc-logo.png" width="650" alt="google-summer-of-code"></a>
    <br>
    <b> 
        <p>
        Deduplicate and cleanup
 <a href="https://github.com/Homebrew/actions">GitHub Actions </a> on <a href="https://brew.sh/">Homebrew</a>
        </p>
    </b>
</div>

<p align="center">
    <code> 
        <a href="#-project-abstract">Project Summary</a>&nbsp;&nbsp;&nbsp;
        <a href="#-deliverables">Deliverables</a>&nbsp;&nbsp;&nbsp;
        <a href="#-demo">Demo</a>&nbsp;&nbsp;&nbsp;
        <a href="#-contributions">Contributions</a>&nbsp;&nbsp;&nbsp;
        <a href="#-mentors">Mentors</a>&nbsp;&nbsp;&nbsp;
    </code>
</p>

My dream become true! This summer I got a chance to be GSoC contributor for Homebrew Project. I can't believe that I'm going to contribute to one of the open source tool I use every day.

I create this repository for my self-notes, a brief summary report to Homebrew community, as well as to help other students/contributors in the future that wants to know about what do I do in Google Summer of Code.

## ⭐ Project Abstract

[Homebrew](https://github.com/Homebrew) makes extensive use of GitHub Actions. Some of Homebrew workflows are very similar to each other and could be reused within the Homebrew organisation and community. This project will involve learning about Actions workflows in order to find ways to more efficiently use them across Homebrew projects.

## 🚢 Deliverables

This project aims to:

- Grouping an action step by using composite action and reuse it across Homebrew projects.
- Make a concise github action for better readability and troubleshooting for new contributors.
- Make more clear github action for new contributors, by using more descriptive names for action steps instead of multiple runs on each action step.

<!-- **All of the above deliverables were completed within the GSoC period. Yay! 🎉** -->

## 📺 Demo

### WIP

Work in progress
<!-- To be completed during the mid and final evaluation -->

## 📄 Work Plan

There are several plan that I created for this projects,

1. Create a starter composite action to group bottles result ([Done](https://github.com/Homebrew/actions/pull/289))
2. Apply the starter composite action to homebrew-core github action ([In-Progress](https://github.com/Homebrew/homebrew-core/pull/106155))
   - Working on fix in my [fork repository](https://github.com/mohzulfikar-orgz/homebrew-core-testing/tree/dispatch-action-test)
   - The cause of the failing CI on Linux is because of custom workdir defined on the job matrix.
   - Workaround for this is to modify the composite action to accept inputs that states the working directory from main github action.
   - I opened up a [Pull Request](https://github.com/Homebrew/actions/pull/291) to add this functionality on the [actions repository](https://github.com/Homebrew/actions).
   - After the composite action change had been merged we could direcly use that as a replacement for current repeatable CI steps.
3. Create a Yaml Linter Action (or job) to lint all github action on Homebrew repository. It will triggered if there's any contribution on the repository's Action (In-Progress)
   - Based on Research, Validating Github Action is not just as simple as using any existing yaml linter. Github Action have special format and schema for their own yaml.
   - The Schema of common custom yaml could be found on [schemastore](https://www.schemastore.org/json/) including [Github Action yaml schema](https://json.schemastore.org/github-action.json).
   - Based on Research, I found a possible linters that could lint by using the schema on [schemastore](https://www.schemastore.org/json/). The possible linters are [v8r](https://github.com/chris48s/v8r) (NPM Packages). I need to research more on using this linters and creating a configurations locally.
   - After that, I'll do the testing on my fork repository of [Homebrew/actions](https://github.com/mohzulfikar/actions-homebrew).
   - Before creating a PR, should we open a new [Issue](https://github.com/Homebrew/actions/issues) on action repository?
   - We'll see the result of linting on my fork repository and open a PR to discuss if there's any feedback regarding the errors found on linted file(s).
4. Expand the starter composite action based on discussion.
   - Is it possible to expand the current composite action to support common pattern of `touch`, `cat`, and `rm`?
   - Expand it to include the `brew test-bot` with custom params.
   - Add inputs to choose which file should be applied the operations (`touch`, `cat`, `rm`)
   - Apply on [homebrew-core](https://github.com/Homebrew/homebrew-core) and [homebrew-test-bot](https://github.com/Homebrew/homebrew-test-bot/blob/9c3a37b30e2db946c5da79b5d2f5d1c57e9129ae/.github/workflows/tests.yml) repository.
5. Create second composite action.
   - Grouping the upload, delete, count bottles, and post cleanup steps.

> Additionally, a detailed timeline can be found on [TIMELINE.md](TIMELINE.md)

## 🚀 Contributions

### PRs

<div align="center">

| PR Link   | Description  | Status | 
| :-----------: | :------------------------------------:| :------:|
| [bottles-failure-and-output](https://github.com/Homebrew/actions/pull/289) | Create a composite action to group outputs after creating a bottles. | <span style="color:#8957e5">Merged</span>
| [Update github actions to use composite action created before](https://github.com/Homebrew/homebrew-core/pull/106155) | Modify the github action to use the composite action I created on previous [PR](https://github.com/Homebrew/actions/pull/289). |<span style="color:#238636">Open</span>|
| [Update bottles failure and output composite action](https://github.com/Homebrew/actions/pull/291) | I propose the approach to use inputs to make the composite action runs on custom workdir. This will solve the failing CI on this [PR](https://github.com/Homebrew/actions/pull/289) | <span style="color:#238636">Open</span>

</div>

### Issues
    

<div align="center">
    
| Issue Link   | Description  | Status | 
| :-----------: | :------------------------------------:| :------:|
| [ISSUE #44](https://github.com/Homebrew/gsoc/issues/44) on [GSoC](https://github.com/Homebrew/gsoc) | [Project Submission] Deduplicate and cleanup GitHub Actions | WIP |
| [ISSUE #11101](https://github.com/Homebrew/brew/issues/11101) on [brew](https://github.com/Homebrew/brew) | [IMPROVEMENT] Deduplicate GitHub Actions Usage | WIP |

</div>
    
<!-- ### My overall contributions at Rocket.Chat -->
    
<!-- ## 😎 Blog -->
    
<!-- TODO -->

## 🎓 Mentors

A big big thank you to my mentors for the support and guidaince before and throughout GSoC working period. 🙏 
    
I learned beyond GSoC from them and am forever grateful to be mentored by them.

- **Misty De Méo** - [GitHub](https://github.com/mistydemeo).


<!-- ## 🔗 Links -->

<!-- - Read my Poll App project proposal that got me accepted to GSoC [here](). -->

<!-- ## ❤️ Support

Thank you for reading this documents. Consider for a visit to my blog or give this repo a star ⭐ and watch 👁️ so you don't miss if there's some updates. -->
    
<!-- ## 💬 Connect With Me -->
