# project-flow-set-pr-assignees-and-reviewers

## 개요

이 액션은 PR이 생성될 때 지정된 assignees와 reviewer를 자동으로 등록합니다.

---

## ✨ 기능 설명

- PR이 생성될 때 PR의 숫자를 얻어옵니다.
- 지정한 assignee와 reviewer를 PR에 설정합니다.
- assignees를 설정하지 않으면 기본적으로 PR을 생성한 유저가 할당됩니다
- assignees와 reviewers 모두 입력을 쉼표로 구분합니다.
- team_reviewers 입력을 지원하며 지정한 팀원이 reviewer로 지정됩니다.

## 🧾 입력값

| 이름             | 필수 여부 | 기본값    | 설명                                                                |
| ---------------- | --------- | --------- | ------------------------------------------------------------------- |
| `github_token`   | 예        | –         | GitHub Token (예: PAT 또는 GITHUB_TOKEN)                            |
| `assignees`      | 아니오    | PR 생성자 | 유저 이름을 쉼표로 구분하여 입력하세요. (예: user1,user2)           |
| `reviewers`      | 아니오    | –         | 리뷰어 이름을 쉼표로 구분하여 입력하세요. (예: reviewer1,reviewer2) |
| `team_reviewers` | 아니오    | –         | 팀 이름을 쉼표로 구분하여 입력하세요. (예: team1,team2)             |

---

## 🔁 사용 예시

```yaml
on:
  pull_request:
    types: [opened]

jobs:
  set-pr-assignees-and-reviewers:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Sync Issue Metadata to PR
        uses: jinhokim98/project-flow-set-pr-assignees-and-reviewers@v1
        with:
          github_token: ${{ secrets.PERSONAL_TOKEN }}
          assignees: jinhokim98
          reviewers: reviewer1,reviewer2
          team_reviewers: teamReviewer
```

# project-flow-set-pr-assignees-and-reviewers

## Overview

This GitHub Action automatically assigns specified assignees and reviewers when a pull request (PR) is opened.

---

## ✨ Features

- Automatically retrieves the PR number when a PR is created.
- Assigns specified users as assignees and reviewers to the PR.
- If no assignees are provided, the PR author will be assigned by default.
- Both `assignees` and `reviewers` inputs support comma-separated lists.
- Supports `team_reviewers` to assign GitHub teams as reviewers.

---

## 🧾 Inputs

| Name             | Required | Default   | Description                                                   |
| ---------------- | -------- | --------- | ------------------------------------------------------------- |
| `github_token`   | Yes      | –         | GitHub Token (e.g., PAT or GITHUB_TOKEN)                      |
| `assignees`      | No       | PR author | Comma-separated list of assignees (e.g., user1,user2)         |
| `reviewers`      | No       | –         | Comma-separated list of reviewers (e.g., reviewer1,reviewer2) |
| `team_reviewers` | No       | –         | Comma-separated list of team names (e.g., team1,team2)        |

---

## 🔁 Usage Example

```yaml
on:
  pull_request:
    types: [opened]

jobs:
  set-pr-assignees-and-reviewers:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Sync Issue Metadata to PR
        uses: jinhokim98/project-flow-set-pr-assignees-and-reviewers@v1
        with:
          github_token: ${{ secrets.PERSONAL_TOKEN }}
          assignees: jinhokim98
          reviewers: reviewer1,reviewer2
          team_reviewers: teamReviewer
```
