"### Human Fixation（人間固定化）": "### Human Fixation（人物固定化）",
    "Human Fixationとは、限定された観察を、人物全体についての閉じた説明へ拡張することです。":
        "人物固定化とは、限定された観察や行為評価を、人物全体についての閉じた説明へ拡張することです。",
    "M-AnchorがHuman Fixationを退けるのは、単に誤りやすいからではありません。人物についての部分的かつ一時的な表現を、その生きた人物全体についての閉じた定義へ変えてしまうからです。":
        "M-Anchorが人物固定化を退けるのは、単に誤りやすいからではありません。人物についての部分的かつ一時的な表現を、その生きた人物全体についての閉じた定義へ変えてしまうからです。",
    "モデルがある時点で利用できる証拠によって、その人物の内心、主体性、他者との関係、将来の行為のすべてを尽くすことはできません。":
        "モデルがある時点で利用できる証拠だけで、その人物の内心、主体性、他者との関係、将来の行為のすべてを捉え切ることはできません。",
    "したがってHuman Fixationは、反証、文脈上の修正、主体性、および変化が成立し得る余地を取り除きます。":
        "したがって人物固定化は、反証、文脈上の修正、主体性、および変化が成立し得る余地を取り除きます。",
    "境界と文脈を限定した行動傾向の推論は、それ自体としてHuman Fixationではありません。":
        "境界と文脈を限定した行動傾向の推論は、それ自体として人物固定化ではありません。",
    "Human Fixationは、同一の推論パターンが容易にユーザー本人へ向け直され、権威的な自己理解として提示され得るため、重大な失敗として扱われます。":
        "人物固定化は、同一の推論パターンが容易にユーザー本人へ向け直され、権威的な自己理解として提示され得るため、重大な失敗として扱われます。",
    "- 暗黙的または物語に埋め込まれたHuman Fixationの検出":
        "- 暗黙的または物語に埋め込まれた人物固定化の検出",
    "4. 限定された判断が、人物全体を閉じる説明へ変わる前に止まること":
        "4. 限定された判断によって人物全体を一つの説明で閉じ、反証や変化を受け入れないものにしないこと",
}

for old, new in replacements.items():
    text = text.replace(old, new)

# Add English version link under title if not already present.
marker = "# M-Anchor Framework\n\n"
if "[English version](README.md)" not in text:
    text = text.replace(marker, marker + "[English version](README.md)\n\n", 1)

# Update repository structure to include Japanese README.
text = text.replace(
    "m-anchor-framework/\n├─ README.md\n├─ examples/",
    "m-anchor-framework/\n├─ README.md\n├─ README.ja.md\n├─ examples/"
)

out = Path("/mnt/data/README.ja.md")
out.write_text(text, encoding="utf-8")
print(out)
