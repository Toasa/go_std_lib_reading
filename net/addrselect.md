- 概要
    - RFC 6724 は IPv6 の src と dst のアドレスを選出するアルゴリズムを定めている
    - addrselect.go ではそれに準拠したライブラリを提供する
    - ソースを読むと単にアドレスを選出するというより、アドレスの集合に順序を入れる、つまりソートを提供しているようだ
- 実装
    - `sort.Stable()` を使用している
        - `Stable` は引数に `Interface` 構造体を取り、この構造体は以下の三つのメソッドを満たす必要がある
            - `Len() int`
            - `Less(i, j int) bool`
            - `Swap(i, j int)`
        - addrselect.go の `byRFC6724` 構造体でも上三つのメソッドが定義されている
