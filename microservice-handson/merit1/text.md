講義で挙げたマイクロサービスのもう1つのメリットである障害の局所化について説明する。

マイクロサービスは基本疎結合に作られるため、連携していない箇所に影響はしない。

ここではその一例としてrecommendationサービスをダウンしてもショッピングができることを確認する

1. recommendationサービスを停止する
    ```
    docker compose stop recommendationservice
    ```{{exec}}

2. frontendにアクセスする
   - Killercodaでは[こちら]({{TRAFFIC_HOST1_8080}})からアクセスする
   - ローカルで起動している場合は<https://localhost:8080>でアクセスできる

3. お買い物をしても推奨商品が提示されないだけで買い物ができることを確認する。

4. 次のタスクのために再度起動する
    ```
    docker compose start recommendationservice
    ```{{exec}}

障害は局所化される分、きちんと監視やエラーを特定していくことが必要になる。そのためのツールを次から見ていく。