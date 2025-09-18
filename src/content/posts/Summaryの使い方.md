---
title: Summary의 사용방법 Summaryの使い方
published: 2025-09-18
description: Summary를 활용하여 가독성을 늘리기 Summaryを使って可読性を上げる
image: ''
tags: [Unity, C#, Study, Develop]
category: 'C#'
draft: false 
lang: 'ko'
---

# ///Summary에 대하여

Summary는 C#에 있는 주석 기능중 하나, XML 문법을 사용해서 클래스, 메소드, 속성, 필드 등 </br>
코드 작성자의 임의적인 <b>추가 설명 등</b>을 작성하게 할 수 있다.</br>

SummaryはC#にあるコメント機能中一つ、</br>
XML文法を使って、クラス、メソード、プロパティー、フィールドなど</br>
コード作成者の任意的な<b>追加説明</b>を作成することができる。

예시 코드　例コード
```csharp
    public void EnableInteract(InteractableType type)
    {
        switch (type)
        {
            case InteractableType.Hideable:
                ObjectSpriteRenderer = this.GetComponent<SpriteRenderer>();
                ObjectSpriteRenderer.color = new Color(1f, 1f, 1f, 0.3f);
                ObjectSpriteRenderer.sortingOrder = 11;
                break;
            case InteractableType.Collectible:
                //TODO : 아이템 주웠음!! アイテムを拾った！！！
                // Debug.Log("Collectible");
                break;
            case InteractableType.Triggerable:
                triggerable = this.GetComponent<ITriggerable>();
                triggerable.TriggerAction();
                break;
            default:
                Debug.Log("None");
                break;
        }
    }
```

현재 열심히 개발중인 게임의 일부 메소드, 메소드 명과 지역 변수로 어떤 기능인지 추측은 할 수 있으나, 추측만 가능할 뿐 실제로 맞는지에 대해 한번 더 생각하게 된다. <b> 실제로 작성자 또한 나중에 코드를 보고 헷갈릴 수도 있을테니까 </b></br>

現在頑張って開発中の一部のメソード、メソード名とパラメータでどんな機能なのか推測はできるが、</br>
推測ができるだけで実際あってるのかはもう一回考えさせられる。</br> <b>実際作成者もまたコードを見て混乱するかもしれないから。</b>

사용 예시
```csharp
    /// <summary>
    /// 상호작용을 실행하는 메소드
    /// インタレクション（相互作用）を実行するメソード
    /// </summary>
    /// <param name="type"> 실행할 상호작용의 타입을 충돌처리한 오브젝트에서 받아와야 합니다.
    /// <para> 実行するインタレクションのタイプを衝突処理したオブジェクトからもらう必要があります。</para>
    /// </param>
        public void EnableInteract(InteractableType type)
    {
        switch (type)
        {
            case InteractableType.Hideable:
                ObjectSpriteRenderer = this.GetComponent<SpriteRenderer>();
                ObjectSpriteRenderer.color = new Color(1f, 1f, 1f, 0.3f);
                ObjectSpriteRenderer.sortingOrder = 11;
                break;
            case InteractableType.Collectible:
                //TODO : 아이템 주웠음!! 
                // Debug.Log("Collectible");
                break;
            case InteractableType.Triggerable:
                triggerable = this.GetComponent<ITriggerable>();
                triggerable.TriggerAction();
                break;
            default:
                Debug.Log("None");
                break;
        }
    }
```
</br>

# 기본적인 사용법
## ```<summary>```

가장 처음으로는 ```<summary>``` 태그를 붙이는 것, 또는 VSCode의 경우 / 세번 입력으로 공식적으로 지원한다</br>
자세한 것은 VSCode -> Preferences -> Settings -> editor: Format On Type</br>
<b>C# 확장</b>을 설치 했을 경우 기본적으로 사용함으로 되어있다.

最初に ```<summary>``` タグを付けること、またはVSCodeの場合 / 3回入力で公式にサポートする</br>
詳しくはVSCode -> Preferences -> Settings -> editor: Format On Type</br>
<b>C# 拡張</b>を設置した場合、基本的に使用することになっている。

```csharp
///<summary>
/// 기본적인 사용 방법 예시 基本的な使用方法の例
///</summary>
float f;
// 이후 마우스 커서를 f에 올려 놓으면 '기본적인 사용 방법 예시' 가 팝업된다.　
// 以後、マウスカーソルをf に置くと、「基本的な使用方法の例」がポップアップされる。
```

```csharp
///<summary>
/// 메소드에 관한 설명　メソッドに関する説明
///</summary>
void Method()
{

}
// 이후 마우스 커서를 method()에 올려 놓으면 '메소드에 관한 설명'이 팝업된다.　
// 以後、マウスカーソルをメソッド()に置くと、「メソッドに関する説明」がポップアップされる。
```

```csharp
///<summary>
/// 속성에 관한 설명 プロパティー関する説明
///</summary>
string? Properties { get; set; }
// 이후 마우스 커서를 Properties에 올려 놓으면 '속성에 관한 설명'이 팝업된다.　
// 以後、マウスカーソルをPropertiesに置くと「プロパティー関する説明」がポップアップされる。
```

```csharp
///<summary>
/// 필드에 관한 설명　フィールドに関する説明
/// </summary>
private float field;
// 이후 마우스 커서를 field에 올려놓으면 '필드에 관한 설명' 이 팝업된다.　
// 以後、マウスカーソルをfieldに置くと、「フィールドに関する説明」がポップアップされる。
```

이런 식으로 추가적인 설명을 추가할 각 요소의 위에 작성을 해주면 된다.</br>
줄바꿈의 경우 기본적으로 XML,HTML과 동일하게 `</br>` 이후 내용 또는,  `<para>` 줄바꿈 내용 `</para>`이 가능하다.

このように追加的な説明を追加する各要素の上に作成すれば良い。</br>
改行の場合、基本的にXML、HTMLと同様に`</br>`以降の内容または`<para>`改行内容`</para>`が可能である。

```csharp
///<summary>
/// 필드에 관한 설명 フィールドに関する説明</br>
/// 필드에 관한 설명2　フィールドに関する説２
/// <para> 필드에 관한 설명3 フィールドに関する説３</para>
/// </summary>
private float field;
// 이후 마우스 커서를 field에 올려놓으면　以後、マウスカーソルをfieldに置くと、
// 필드에 관한 설명　フィールドに関する説明
// 필드에 관한 설명2　フィールドに関する説明２
// 필드에 관한 설명3　フィールドに関する説明３
// 이 팝업된다.　がポップアップされる。
```

## ```<param>```

다음으로는 `<param>`이다. 이것은 메소드 등에서 매개변수가 주어졌을 때, 그 매개변수에 대한 설명을 적는 기능이다.</br>
사용법은 `</summary>` 태그의 아래에 추가로 작성하는 식으로 작성한다.

次は`<param>`だ。 これはメソッド等でパラメータが与えられたとき</br>
そのパラメータについての説明を書く機能である。</br>
使い方は`</summary>`タグの下に追加で作成する方式で作成する。

```csharp
///<summary>
/// 메소드에 대한 설명　メソッドに関する説明
/// </summary>
/// <param name="parameter"> 매개 변수 'parameter'에 대한 설명　パラメーター「parameter」に関する説明
/// </param>
public void Method(int parameter)
// parameter에 마우스 커서를 올리면 "매개 변수 'parameter'에 대한 설명" 이 팝업된다.　
// 以後、マウスカーソルを「parameter」に置くと、パラメーター「parameter」に関する説明がポップアップされる
{

}
```
이런 느낌. 위의 개발중인 게임의 일부 코드에도 비슷한 느낌으로 작성되어 있다.
こんな感じ、上に開発中のゲームの一部コードにも似たような感じで書いている。


## ```<return>```
이건 아직까지는 사용해본 적은 없으나, 일단은 공부해둔 것이기때문에 작성</br>
return값이 존재할 때, 그에 대한 설명을 적는 태그다.</br>

これはまだ使ったことはないけど、一応勉強していたもので書く</br>
リータンステートメントが存在する場合、それに関する説明を書くタグである。

```csharp
///<summary>
/// 더하기 연산　足し算
/// </summary>
/// <param name="a"> </param>
/// <param name="b"> </param>
/// <returns>a b를 더한 값을 반환 aとｂを足した値を返還</returns>
public int Add(int a, int b)
{
    return a+b;
}
// Add에 마우스 커서를 올리면 '더하기 연산' 아래에 'a b를 더한 값을 반환'이 추가되어서 나온다.
// Addにマウスカーソルを上げると、「足す演算」の下に「abを足した値を返す」が追加されて出てくる。
```

