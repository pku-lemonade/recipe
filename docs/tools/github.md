# GitHub 相关

实验室主要使用 `GitHub` 来管理项目代码和同步科研进度。在熟悉`git`的基本操作后，还需要熟悉 `Pull Request` 流程。

## Pull Request

Git 作为一个代码管理系统，最重要的功能就是多人协作。协作必须要有一个规范的**流程**来保证效率。Pull Request（PR）就是 Github 上的一种流程。可以参考[这个](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests)官方教程。

因为 PR 流程非常重要，而且这个教程的中文翻译太差，所以我们在这里专门介绍一下。

0. Github 默认创建了 `main` 分支。所有 commit 的最终目的都是合并进入 `main` 分支。
1. 当需要实现新功能时，先从 `main` 分支创建一个新的分支，并给分支取一个有意义的名字。比如，`test-single-thread`，`fix-readme-typo`，`add-xxx-test-case` 等。在新分支上创建 commit。
2. 当新功能在新分支上开发完成后，将分支 push 到远程仓库。
3. 在 Github 上，点击 `New pull request`，选择 `base` 为 `main` 分支，`compare` 选择新分支，然后点击 `Create pull request`，并且为你的 PR 选择一个有意义的名字，这个名字应该是分支名对应的一个完整的句子。
4. 当 PR 创建后，选择 Reviewers 通知相关的同学。
5. 作为 Reviewer，如果你觉得 PR 可以合并，那么点击 `Approve`。如果你觉得 PR 还有问题，那么你可以在评论中写明你的意见，并且点击 `Request changes`。这样，提交者就会收到通知，需要修改代码。如果你不确定，可以点击 `Comment`，并且在评论中写明你的疑问。在讨论中，你还可以不断提交代码。
6. 当 PR 被通过后，代码会被合并到 `main` 分支中。创建的新分支可以删除了（因为根据第 1 条，每个分支的名字应该有意义。在一次合并完成后，不应该继续使用这个分支）
7. 当需要再次实现新功能并提交 PR 的时候，记得先更新合并后的 `main` 分支，从最新的 `main` 分支创建一个新的分支。

### Lemonade Review 的规定

在论文阅读时使用 PR 来合并[论文列表](https://github.com/pku-lemonade/new-lemonade-review)。请注意：

1. 每个人每周需要 review 至少一个 PR。
2. 在 review PR 时，如果需要评论，应该点击 `start a review` 而不是`add single comment`，在所有评论结束后再点击 `submit review`，以避免每条评论后都发送一封通知邮件。
