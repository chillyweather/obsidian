# The Perfect Commit

[[Knowledge Base/Web Development/GIT & Command Line/git]]

-   `feat` introduces a new feature to your project. This includes any complete block of code that performs its task. It can be a complete header, footer, news aggregator, etc.
-   `fix` patches a bug in your code. For example, a broken link is an error, and changing styles or HTML are used to fix it.
-   `style` changes the appearance of your code. It has nothing to do with adding new features, and doesn't affect the meaning of the code. This includes whitespace, formatting, missing semicolons, etc.
-   `refactor` restructures your code. It neither fixes a bug nor adds a new feature. Example: changing the order of writing CSS properties in selectors, or breaking a JS function into several smaller ones. You can specify the type of your commit even further by adding a scope in parentheses. For example, feat(search bar). This is optional though.



## [](https://www.conventionalcommits.org/en/v1.0.0/#summary)Summary

The Conventional Commits specification is a lightweight convention on top of commit messages. It provides an easy set of rules for creating an explicit commit history; which makes it easier to write automated tools on top of. This convention dovetails with [SemVer](http://semver.org/), by describing the features, fixes, and breaking changes made in commit messages.

The commit message should be structured as follows:

___

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

___

The commit contains the following structural elements, to communicate intent to the consumers of your library:

1.  **fix:** a commit of the _type_ `fix` patches a bug in your codebase (this correlates with [`PATCH`](http://semver.org/#summary) in Semantic Versioning).
2.  **feat:** a commit of the _type_ `feat` introduces a new feature to the codebase (this correlates with [`MINOR`](http://semver.org/#summary) in Semantic Versioning).
3.  **BREAKING CHANGE:** a commit that has a footer `BREAKING CHANGE:`, or appends a `!` after the type/scope, introduces a breaking API change (correlating with [`MAJOR`](http://semver.org/#summary) in Semantic Versioning). A BREAKING CHANGE can be part of commits of any _type_.
4.  _types_ other than `fix:` and `feat:` are allowed, for example [@commitlint/config-conventional](https://github.com/conventional-changelog/commitlint/tree/master/%40commitlint/config-conventional) (based on the [the Angular convention](https://github.com/angular/angular/blob/22b96b9/CONTRIBUTING.md#-commit-message-guidelines)) recommends `build:`, `chore:`, `ci:`, `docs:`, `style:`, `refactor:`, `perf:`, `test:`, and others.
5.  _footers_ other than `BREAKING CHANGE: <description>` may be provided and follow a convention similar to [git trailer format](https://git-scm.com/docs/git-interpret-trailers).

Additional types are not mandated by the Conventional Commits specification, and have no implicit effect in Semantic Versioning (unless they include a BREAKING CHANGE). A scope may be provided to a commit’s type, to provide additional contextual information and is contained within parenthesis, e.g., `feat(parser): add ability to parse arrays`.

## [](https://www.conventionalcommits.org/en/v1.0.0/#examples)Examples

### [](https://www.conventionalcommits.org/en/v1.0.0/#commit-message-with-description-and-breaking-change-footer)Commit message with description and breaking change footer

```
feat: allow provided config object to extend other configs

BREAKING CHANGE: `extends` key in config file is now used for extending other config files
```

### [](https://www.conventionalcommits.org/en/v1.0.0/#commit-message-with--to-draw-attention-to-breaking-change)Commit message with `!` to draw attention to breaking change

```
refactor!: drop support for Node 6
```

### [](https://www.conventionalcommits.org/en/v1.0.0/#commit-message-with-scope-and--to-draw-attention-to-breaking-change)Commit message with scope and `!` to draw attention to breaking change

```
refactor(runtime)!: drop support for Node 6
```

### [](https://www.conventionalcommits.org/en/v1.0.0/#commit-message-with-both--and-breaking-change-footer)Commit message with both `!` and BREAKING CHANGE footer

```
refactor!: drop support for Node 6

BREAKING CHANGE: refactor to use JavaScript features not available in Node 6.
```

### [](https://www.conventionalcommits.org/en/v1.0.0/#commit-message-with-no-body)Commit message with no body

```
docs: correct spelling of CHANGELOG
```

### [](https://www.conventionalcommits.org/en/v1.0.0/#commit-message-with-scope)Commit message with scope

```
feat(lang): add polish language
```

### [](https://www.conventionalcommits.org/en/v1.0.0/#commit-message-with-multi-paragraph-body-and-multiple-footers)Commit message with multi-paragraph body and multiple footers

```
fix: correct minor typos in code

see the issue for details

on typos fixed.

Reviewed-by: Z
Refs #133
```

## [](https://www.conventionalcommits.org/en/v1.0.0/#specification)Specification

The key words “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “MAY”, and “OPTIONAL” in this document are to be interpreted as described in [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt).

1.  Commits MUST be prefixed with a type, which consists of a noun, `feat`, `fix`, etc., followed by the OPTIONAL scope, OPTIONAL `!`, and REQUIRED terminal colon and space.
2.  The type `feat` MUST be used when a commit adds a new feature to your application or library.
3.  The type `fix` MUST be used when a commit represents a bug fix for your application.
4.  A scope MAY be provided after a type. A scope MUST consist of a noun describing a section of the codebase surrounded by parenthesis, e.g., `fix(parser):`
5.  A description MUST immediately follow the colon and space after the type/scope prefix. The description is a short summary of the code changes, e.g., _fix: array parsing issue when multiple spaces were contained in string_.
6.  A longer commit body MAY be provided after the short description, providing additional contextual information about the code changes. The body MUST begin one blank line after the description.
7.  A commit body is free-form and MAY consist of any number of newline separated paragraphs.
8.  One or more footers MAY be provided one blank line after the body. Each footer MUST consist of a word token, followed by either a `:<space>` or `<space>#` separator, followed by a string value (this is inspired by the [git trailer convention](https://git-scm.com/docs/git-interpret-trailers)).
9.  A footer’s token MUST use `-` in place of whitespace characters, e.g., `Acked-by` (this helps differentiate the footer section from a multi-paragraph body). An exception is made for `BREAKING CHANGE`, which MAY also be used as a token.
10.  A footer’s value MAY contain spaces and newlines, and parsing MUST terminate when the next valid footer token/separator pair is observed.
11.  Breaking changes MUST be indicated in the type/scope prefix of a commit, or as an entry in the footer.
12.  If included as a footer, a breaking change MUST consist of the uppercase text BREAKING CHANGE, followed by a colon, space, and description, e.g., _BREAKING CHANGE: environment variables now take precedence over config files_.
13.  If included in the type/scope prefix, breaking changes MUST be indicated by a `!` immediately before the `:`. If `!` is used, `BREAKING CHANGE:` MAY be omitted from the footer section, and the commit description SHALL be used to describe the breaking change.
14.  Types other than `feat` and `fix` MAY be used in your commit messages, e.g., _docs: updated ref docs._
15.  The units of information that make up Conventional Commits MUST NOT be treated as case sensitive by implementors, with the exception of BREAKING CHANGE which MUST be uppercase.
16.  BREAKING-CHANGE MUST be synonymous with BREAKING CHANGE, when used as a token in a footer.

## [](https://www.conventionalcommits.org/en/v1.0.0/#why-use-conventional-commits)Why Use Conventional Commits

-   Automatically generating CHANGELOGs.
-   Automatically determining a semantic version bump (based on the types of commits landed).
-   Communicating the nature of changes to teammates, the public, and other stakeholders.
-   Triggering build and publish processes.
-   Making it easier for people to contribute to your projects, by allowing them to explore a more structured commit history.

## [](https://www.conventionalcommits.org/en/v1.0.0/#faq)FAQ

### [](https://www.conventionalcommits.org/en/v1.0.0/#how-should-i-deal-with-commit-messages-in-the-initial-development-phase)How should I deal with commit messages in the initial development phase?

We recommend that you proceed as if you’ve already released the product. Typically _somebody_, even if it’s your fellow software developers, is using your software. They’ll want to know what’s fixed, what breaks etc.

### [](https://www.conventionalcommits.org/en/v1.0.0/#are-the-types-in-the-commit-title-uppercase-or-lowercase)Are the types in the commit title uppercase or lowercase?

Any casing may be used, but it’s best to be consistent.

### [](https://www.conventionalcommits.org/en/v1.0.0/#what-do-i-do-if-the-commit-conforms-to-more-than-one-of-the-commit-types)What do I do if the commit conforms to more than one of the commit types?

Go back and make multiple commits whenever possible. Part of the benefit of Conventional Commits is its ability to drive us to make more organized commits and PRs.

### [](https://www.conventionalcommits.org/en/v1.0.0/#doesnt-this-discourage-rapid-development-and-fast-iteration)Doesn’t this discourage rapid development and fast iteration?

It discourages moving fast in a disorganized way. It helps you be able to move fast long term across multiple projects with varied contributors.

### [](https://www.conventionalcommits.org/en/v1.0.0/#might-conventional-commits-lead-developers-to-limit-the-type-of-commits-they-make-because-theyll-be-thinking-in-the-types-provided)Might Conventional Commits lead developers to limit the type of commits they make because they’ll be thinking in the types provided?

Conventional Commits encourages us to make more of certain types of commits such as fixes. Other than that, the flexibility of Conventional Commits allows your team to come up with their own types and change those types over time.

### [](https://www.conventionalcommits.org/en/v1.0.0/#how-does-this-relate-to-semver)How does this relate to SemVer?

`fix` type commits should be translated to `PATCH` releases. `feat` type commits should be translated to `MINOR` releases. Commits with `BREAKING CHANGE` in the commits, regardless of type, should be translated to `MAJOR` releases.

### [](https://www.conventionalcommits.org/en/v1.0.0/#how-should-i-version-my-extensions-to-the-conventional-commits-specification-eg-jameswomackconventional-commit-spec)How should I version my extensions to the Conventional Commits Specification, e.g. `@jameswomack/conventional-commit-spec`?

We recommend using SemVer to release your own extensions to this specification (and encourage you to make these extensions!)

### [](https://www.conventionalcommits.org/en/v1.0.0/#what-do-i-do-if-i-accidentally-use-the-wrong-commit-type)What do I do if I accidentally use the wrong commit type?

#### [](https://www.conventionalcommits.org/en/v1.0.0/#when-you-used-a-type-thats-of-the-spec-but-not-the-correct-type-eg-fix-instead-of-feat)When you used a type that’s of the spec but not the correct type, e.g. `fix` instead of `feat`

Prior to merging or releasing the mistake, we recommend using `git rebase -i` to edit the commit history. After release, the cleanup will be different according to what tools and processes you use.

#### [](https://www.conventionalcommits.org/en/v1.0.0/#when-you-used-a-type-not-of-the-spec-eg-feet-instead-of-feat)When you used a type _not_ of the spec, e.g. `feet` instead of `feat`

In a worst case scenario, it’s not the end of the world if a commit lands that does not meet the Conventional Commits specification. It simply means that commit will be missed by tools that are based on the spec.

### [](https://www.conventionalcommits.org/en/v1.0.0/#do-all-my-contributors-need-to-use-the-conventional-commits-specification)Do all my contributors need to use the Conventional Commits specification?

No! If you use a squash based workflow on Git lead maintainers can clean up the commit messages as they’re merged—adding no workload to casual committers. A common workflow for this is to have your git system automatically squash commits from a pull request and present a form for the lead maintainer to enter the proper git commit message for the merge.

### [](https://www.conventionalcommits.org/en/v1.0.0/#how-does-conventional-commits-handle-revert-commits)How does Conventional Commits handle revert commits?

Reverting code can be complicated: are you reverting multiple commits? if you revert a feature, should the next release instead be a patch?

Conventional Commits does not make an explicit effort to define revert behavior. Instead we leave it to tooling authors to use the flexibility of _types_ and _footers_ to develop their logic for handling reverts.

One recommendation is to use the `revert` type, and a footer that references the commit SHAs that are being reverted:

```
revert: let us never again speak of the noodle incident

Refs: 676104e, a215868
```