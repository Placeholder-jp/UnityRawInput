UnityRawInputをforkして改造しました

## 変更点

UnityのInputのインターフェースに合わせて、以下のメソッドを追加しています

```
RawKeyInput.GetKeyDown(RawKey key)
```
```
RawKeyInput.GetKey(RawKey key)
```
```
RawKeyInput.GetKeyUp(RawKey key)
```

## 使い方

以下サンプルです

```
public class Sample : MonoBehaviour
{
    private void OnEnable()
    {
        RawKeyInput.Start(true);
    }

    private void Update()
    {
        if (RawKeyInput.GetKeyDown(RawKey.Space))
        {
            Debug.LogFormat("[RawInput] GetKeyDown");
        }

        if (RawKeyInput.GetKey(RawKey.Space))
        {
            Debug.LogFormat("[RawInput] GetKey");
        }

        if (RawKeyInput.GetKeyUp(RawKey.Space))
        {
            Debug.LogFormat("[RawInput] GetKeyUp");
        }
    }

    private void LateUpdate()
    {
        RawKeyInput.LateUpdate();
    }

    private void OnDisable()
    {
        RawKeyInput.Stop();
    }
}
```

本家にない以下の呼び出しが必要になりました

```
RawKeyInput.LateUpdate()
```
