# Пример непонятно чего

```cpp
struct DSU {

    vector<int> parent;
    vector<int> size;

    DSU(int n) {
        parent.resize(n);
        size.resize(n, 1);
        for (int i = 0; i < n; i++) { parent[i] = i; }
    }

    int get_root(int elem) {
        if (parent[elem] == elem) { return elem; }
        return parent[elem] = get_root(parent[elem]);
    }

    bool unite(int elem_1, int elem_2) {
        int root_1 = get_root(elem_1);
        int root_2 = get_root(elem_2);

        if (root_1 == root_2) { return false; }

        if (size[root_1] > size[root_2]) { swap(root_1, root_2); }
        parent[root_1] = root_2;
        size[root_2] += size[root_1];

        return true;
    }
};
```
