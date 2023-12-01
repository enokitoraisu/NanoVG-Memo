# NanoVG-Memo

ForgeだとnvgCreateする場所によってはInvalid operationになる

(安定はMinecraftのinit (1.8.9とはかstartGame)の最後)

# ByteBufferのお話

なぜかローカル変数だとメモリエラー起きる

## エラー起きるコード
```java
public class Loader {
  public Loader(long nvg) {
    ByteBuffer buffer = ...;
    NanoVG.nvgCreateFontMem(nvg, "FONT_NAME", buffer, 0);
  }
}
```

## エラー起きないコード
```java
public class Loader {
  private ByteBuffer buffer;

  public Loader(long nvg) {
    this.buffer = ...;
    NanoVG.nvgCreateFontMem(nvg, "FONT_NAME", buffer, 0);
  }
}
```

# なんかぼやける

floatのxとyを(int)でキャストしちゃいましょう

なんとぼやけません!
