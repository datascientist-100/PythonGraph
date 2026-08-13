
## 
https://www.facebook.com/story.php?story_fbid=1576332137296137&id=100047580963457

https://chatgpt.com/share/6a75685f-8c64-83ee-bede-5bc6c5d56bd9

このグラフは、左右に横棒グラフを配置した 「バタフライチャート（Butterfly chart）」、または 「トルネードチャート」 と呼ばれる形式です。

Pythonでは matplotlib で、左グラフ・中央ラベル・右グラフの3列に分けるとかなりきれいに再現できます。
```
import matplotlib.pyplot as plt
import numpy as np

# -----------------------------
# データ
# -----------------------------
categories = [
    "Grant writing",
    "Marketing and communications",
    "Policy and advocacy",
    "Board and governance reporting",
    "Operations",
    "Programme and service delivery",
    "Impact reporting",
    "Fundraising campaigns",
    "Stakeholder engagement",
    "Information technology",
    "Finance",
    "Human resources",
    "Legal",
    "Tax and compliance",
]

left_values = [42, 39, 28, 24, 22, 22, 22, 21, 15, 13, 12, 11, 6, 6]
right_values = [52, 52, 36, 33, 30, 32, 26, 21, 27, 24, 10, 16, 9, 9]

y = np.arange(len(categories))


# -----------------------------
# グラフ作成
# -----------------------------
fig, (ax_left, ax_center, ax_right) = plt.subplots(
    ncols=3,
    figsize=(14, 7),
    gridspec_kw={
        "width_ratios": [1, 1.15, 1],
        "wspace": 0.02
    }
)

# 色
bar_color = "#123A8C"
background_color = "#E5E5E5"


# =============================
# 左側
# =============================

# 背景バー
ax_left.barh(
    y,
    [100] * len(y),
    color=background_color,
    height=0.8
)

# データバー
ax_left.barh(
    y,
    left_values,
    color=bar_color,
    height=0.8
)

# 左側は軸を反転
ax_left.set_xlim(100, 0)

# 上から並べる
ax_left.set_ylim(len(categories) - 0.5, -0.5)

# 値ラベル
for i, value in enumerate(left_values):
    ax_left.text(
        value + 2,
        i,
        str(value),
        va="center",
        ha="right",
        fontsize=11
    )

# タイトル
ax_left.set_title(
    "Could benefit most from AI¹",
    fontsize=14,
    fontweight="bold"
)

# 100表示
ax_left.text(
    100,
    -0.9,
    "100",
    ha="left",
    va="center",
    fontsize=11,
    color="gray"
)

# 軸などを消す
ax_left.set_xticks([])
ax_left.set_yticks([])

for spine in ax_left.spines.values():
    spine.set_visible(False)


# =============================
# 中央：カテゴリ名
# =============================

ax_center.set_xlim(0, 1)
ax_center.set_ylim(len(categories) - 0.5, -0.5)

for i, category in enumerate(categories):
    ax_center.text(
        0.5,
        i,
        category,
        ha="center",
        va="center",
        fontsize=11
    )

ax_center.axis("off")


# =============================
# 右側
# =============================

# 背景バー
ax_right.barh(
    y,
    [100] * len(y),
    color=background_color,
    height=0.8
)

# データバー
ax_right.barh(
    y,
    right_values,
    color=bar_color,
    height=0.8
)

ax_right.set_xlim(0, 100)
ax_right.set_ylim(len(categories) - 0.5, -0.5)

# 値ラベル
for i, value in enumerate(right_values):
    ax_right.text(
        value + 2,
        i,
        str(value),
        va="center",
        ha="left",
        fontsize=11
    )

# タイトル
ax_right.set_title(
    "Currently using AI²",
    fontsize=14,
    fontweight="bold"
)

# 100表示
ax_right.text(
    100,
    -0.9,
    "100",
    ha="right",
    va="center",
    fontsize=11,
    color="gray"
)

ax_right.set_xticks([])
ax_right.set_yticks([])

for spine in ax_right.spines.values():
    spine.set_visible(False)


# -----------------------------
# 余白調整
# -----------------------------
plt.tight_layout()

plt.show()
```




## Butterfly charts
https://geoffruddock.com/notebooks/data-viz/butterfly-charts/

<img width="477" height="217" alt="image" src="https://github.com/user-attachments/assets/e86956e7-a100-4c1c-be0e-9647018a9b14" />

<img width="794" height="300" alt="image" src="https://github.com/user-attachments/assets/2212cb1d-f765-46bb-bc80-88067bedf9e2" />



