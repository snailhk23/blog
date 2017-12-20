a = [1, 2, 3, 4]
b = [6, 3, 1, 2, 5, 4]
# b根据a的顺序排序
tmp = list(set(a) & set(b))
tmp.sort(key=lambda x: a.index(x))

