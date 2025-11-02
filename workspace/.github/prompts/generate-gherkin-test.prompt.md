---
mode: agent
---

User input:

${file}

# 依頼事項
入力したファイルはシステムの仕様書です。仕様書から、Gherkin記法のBDDテストシナリオを生成してください。

## 入出力
- 入力: 仕様書（AsciiDoc、Markdown、Word、PDF等）
- 出力: Gherkinテストシナリオ（.feature形式）

## ステップ1: 仕様書の分析

仕様書から以下を抽出：

- 機能ID、機能名、機能概要
- 入力条件、出力結果、処理フロー、制約事項
- 画面要素、操作イベント（該当する場合）
- エンドポイント、リクエスト/レスポンス（該当する場合）
- エラーハンドリング、性能要件

## ステップ2: Gherkin形式

```gherkin
# language: ja
Feature: [機能名]
  
  Background:
    Given [共通の前提条件]

  Scenario: [テストケース名]
    Given [事前条件]
    When [アクション]
    Then [期待結果]
    And [追加の期待結果]

  Scenario Outline: [パラメータ化テスト]
    Given [事前条件]
    When <パラメータ>を入力する
    Then <期待結果>が表示される

    Examples:
      | パラメータ | 期待結果 |
      | 値1       | 結果1   |
```

**キーワード**: Feature, Background, Scenario, Scenario Outline, Given, When, Then, And, But, Examples

## ステップ3: テスト観点

以下の観点でシナリオを作成：

- **正常系**: 基本フロー、標準的な入力値
- **異常系**: 未入力、不正な値、権限エラー、ネットワークエラー
- **境界値**: 最小値、最大値、空文字、文字数制限

## ステップ4: 品質基準

- 具体的で明確な条件と期待値
- 各シナリオは独立して実行可能
- ビジネス用語を使用（実装詳細を避ける）
- Given-When-Thenの順序を守る

## ファイル命名規則

```
tests/features/[機能ID]_[機能名].feature
```
例: `F01_user_registration.feature`, `S01_login_screen.feature`

## 実行例

### 例1: ユーザー登録機能

#### 入力（仕様書の抜粋）
```
機能ID: F01
機能名: ユーザー登録
入力: ユーザー名、メールアドレス、パスワード
出力: 登録完了メッセージ、ユーザーID
処理概要: 入力値を検証し、データベースに登録、確認メールを送信
制約: メールアドレスは一意、パスワードは8文字以上
```

#### 出力（Gherkinシナリオ）
```gherkin
# language: ja
Feature: ユーザー登録
  新規ユーザーがアカウントを作成する機能
  
  Background:
    Given ユーザー登録画面が表示されている

  Scenario: 有効な情報で新規登録する
    Given 登録されていないメールアドレス"test@example.com"を使用する
    When ユーザー名"山田太郎"を入力する
    And メールアドレス"test@example.com"を入力する
    And パスワード"Password123"を入力する
    And 登録ボタンをクリックする
    Then 登録完了メッセージが表示される
    And ユーザーIDが発行される
    And 確認メールが送信される

  Scenario: すでに登録済みのメールアドレスで登録を試みる
    Given メールアドレス"existing@example.com"が登録済みである
    When ユーザー名"佐藤花子"を入力する
    And メールアドレス"existing@example.com"を入力する
    And パスワード"Password456"を入力する
    And 登録ボタンをクリックする
    Then エラーメッセージ「このメールアドレスは既に登録されています」が表示される
    And 登録が完了しない

  Scenario: パスワードが短すぎる場合
    Given 登録されていないメールアドレスを使用する
    When ユーザー名"田中一郎"を入力する
    And メールアドレス"tanaka@example.com"を入力する
    And パスワード"Pass12"を入力する
    And 登録ボタンをクリックする
    Then エラーメッセージ「パスワードは8文字以上で入力してください」が表示される
    And 登録が完了しない
```
