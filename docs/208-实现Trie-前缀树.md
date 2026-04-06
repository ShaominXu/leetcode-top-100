# [208. 实现 Trie (前缀树)](https://leetcode.cn/problems/implement-trie-prefix-tree/)

## 思路

Trie 每个节点维护 26 个子节点和结尾标记。
- `insert`：逐字符创建节点
- `search`：逐字符匹配，最后检查结尾标记
- `startsWith`：只需逐字符匹配

时间复杂度：三操作均为 $O(L)$。
空间复杂度：$O(\sum L)$。

## 代码

=== "Python"
    ```python
    class TrieNode:
        def __init__(self):
            self.next = {}
            self.end = False

    class Trie:
        def __init__(self):
            self.root = TrieNode()

        def insert(self, word: str) -> None:
            cur = self.root
            for ch in word:
                if ch not in cur.next:
                    cur.next[ch] = TrieNode()
                cur = cur.next[ch]
            cur.end = True

        def search(self, word: str) -> bool:
            cur = self.root
            for ch in word:
                if ch not in cur.next:
                    return False
                cur = cur.next[ch]
            return cur.end

        def startsWith(self, prefix: str) -> bool:
            cur = self.root
            for ch in prefix:
                if ch not in cur.next:
                    return False
                cur = cur.next[ch]
            return True
    ```

=== "C++"
    ```cpp
    #include <vector>
    #include <string>
    using namespace std;

    class Trie {
    public:
        struct Node {
            vector<Node*> nxt;
            bool end;
            Node() : nxt(26, nullptr), end(false) {}
        };

        Node* root;

        Trie() {
            root = new Node();
        }

        void insert(string word) {
            Node* cur = root;
            for (char ch : word) {
                int c = ch - 'a';
                if (!cur->nxt[c]) cur->nxt[c] = new Node();
                cur = cur->nxt[c];
            }
            cur->end = true;
        }

        bool search(string word) {
            Node* cur = root;
            for (char ch : word) {
                int c = ch - 'a';
                if (!cur->nxt[c]) return false;
                cur = cur->nxt[c];
            }
            return cur->end;
        }

        bool startsWith(string prefix) {
            Node* cur = root;
            for (char ch : prefix) {
                int c = ch - 'a';
                if (!cur->nxt[c]) return false;
                cur = cur->nxt[c];
            }
            return true;
        }
    };
    ```

---

[← 返回站点首页](index.md)
