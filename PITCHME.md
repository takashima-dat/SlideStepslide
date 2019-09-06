# SlideStep

---

SlideStepは、マウス操作のアクションを取り込んだ音ゲーです。
より高いスコアを競ってください。

マウスとスペースキーを使います。

音ゲーはどれも同じような画面構成になりがちですが、
ワンポイント要素を加えるだけで全く違った操作性になります。
マウスの座標による判定を取り入れて、
新しい操作感の音ゲーにしました。

---

Scriptはかなり先生に教えてもらいました。

フォントアセット以外自作です。

フォント
- [Waptia-Light](https://moji-waku.com/waptia/)
- [数式フォント](http://sapphire.hacca.jp/font/sushiki.html)

---
```cs
for (int i = 0; i < fumenlist.Count; i++)
{//譜面から取り出した数値を使ってノートを生成
  float hk = (float)((fumenlist[i].divth) - 1) / fumenlist[i].beatdiv;
  float hu = (float)(fumenlist[i].beatspot) + (hk);
  float nz = hu * kyori;

  GameObject go = null;
  float nx = (-1.35f) + (0.3f * (fumenlist[i].lane));
  switch (fumenlist[i].notecate)
    {
      case 1://普通ノート
        go = Instantiate(Note, new Vector3(nx, -1f, nz), Quaternion.identity);
        break;
      case 2://グリッサンド
        go = Instantiate(GlisNote, new Vector3(nx, -1f, nz), Quaternion.identity);
        break;
      case 3://スライド(チュートリアル)
        Instantiate(SlideNote, new Vector3(nx, -1f, nz), Quaternion.identity);
        break;
      case 4://チュートリアル用普通ノート
        Instantiate(TNote, new Vector3(nx, -1f, nz), Quaternion.identity);
        break;
      case 5://チュートリアル用グリッサンド
        Instantiate(TGlisNote, new Vector3(nx, -1f, nz), Quaternion.identity);
        break;
        default:
        Debug.LogError(i + "番目のデータおかしい");
        break;
            }
  if (go != null)
  {
    go.GetComponent<Notes>().insth = co;
    co++;
  }
}
```
---
end
