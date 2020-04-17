---
title: ユーザー定義型のコーディング |マイクロソフトドキュメント
description: この例では、SQL Server データベースで使用する UDT を実装する方法を示します。 構造体として UDT を実装します。
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- validation [CLR integration]
- UDTs [CLR integration], coding
- UserDefined serialization format [CLR integration]
- Point UDT
- Parse method
- null values [CLR integration]
- ToString method
- ValidatePoint method
- attributes [CLR integration]
- coding user-defined types [CLR integration]
- Read method
- Write method
- nullability [CLR integration]
- user-defined types [CLR integration], coding
- Currency UDT
- validating UDT values
- exposing UDT properties [CLR integration]
ms.assetid: 1e5b43b3-4971-45ee-a591-3f535e2ac722
author: rothja
ms.author: jroth
ms.openlocfilehash: a9d51cc0c33c8b656df176baa606a88a542ca4bc
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81486959"
---
# <a name="creating-user-defined-types---coding"></a>ユーザー定義型の作成 - コーディング
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  ユーザー定義型 (UDT) の定義をコーディングする際は、形式やシリアル化のオプションを選択するだけでなく、UDT をクラスと構造体のどちらで実装するかによって、さまざまな機能を実装する必要があります。  
  
 このセクションの例では **、Point** UDT を**構造体**(または Visual Basic の**構造体**) として実装する方法を示します。 **ポイント**UDT は、プロパティ プロシージャとして実装された X 座標と Y 座標で構成されます。  
  
 UDT の定義に必要な名前空間を次に示します。  
  
```vb  
Imports System  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
```  
  
```csharp  
using System;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
```  
  
 名前空間**には**、UDT のさまざまな属性に必要なオブジェクトが含まれ、**名前空間**にはアセンブリで使用できるネイティブ データ型を表す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クラスが含まれています。 それ以外にもアセンブリが正しく機能するために必要な名前空間が存在する場合があります。 **ポイント**UDT は、文字列を操作するために**System.Text**名前空間も使用します。  
  
> [!NOTE]  
>  **/clr:pure**でコンパイルされた UDT などの Visual C++ データベース オブジェクトは、実行に対してサポートされていません。  
  
## <a name="specifying-attributes"></a>属性の指定  
 UDT のストレージ表現を構築し、クライアントに UDT を値として転送するためにシリアル化を使用する方法は、属性で決まります。  
  
 属性**が**必要です。 **シリアル化可能属性**は省略可能です。 UDT の戻り値の型に関する情報を提供するために **、Microsoft.SqlServer.Server.SqlFacet 属性**を指定することもできます。 詳細については、「[CLR ルーチンのカスタム属性](../../relational-databases/clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md)」を参照してください。  
  
### <a name="point-udt-attributes"></a>Point UDT の属性  
 **をネイティブにポイント**UDT のストレージ**形式を設定****します**。 **IsByteOrdered**は**true**に設定され、SQL Server では、マネージ コードで同じ比較が行われた場合と同じ比較結果が確実に実行されます。 UDT は、UDT を null に対応させるためにインターフェイスを実装**します**。  
  
 次のコードは、**ポイント**UDT の属性を示しています。  
  
```vb  
<Serializable(), SqlUserDefinedTypeAttribute(Format.Native, _  
  IsByteOrdered:=True)> _  
  Public Structure Point  
    Implements INullable  
```  
  
```csharp  
[Serializable]  
[Microsoft.SqlServer.Server.SqlUserDefinedType(Format.Native,  
  IsByteOrdered=true)]  
public struct Point : INullable  
{  
```  
  
## <a name="implementing-nullability"></a>NULL 値の許容属性の実装  
 アセンブリの属性を正しく指定することに加えて、UDT で NULL 値の許容属性をサポートする必要があります。 にロードされる UDT[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は NULL を認識しますが、UDT が NULL 値を認識するには、UDT が**System.Data.SqlTypes.INullable**インターフェイスを実装する必要があります。  
  
 値が CLR コード内から null かどうかを判断するために必要な**IsNull**というプロパティを作成する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では UDT が NULL インスタンスであることを検出すると、通常の NULL 値処理メソッドを使用して UDT を保存します。 そのため、サーバーが NULL の UDT の不要なシリアル化やシリアル化解除に時間を費やしたり、NULL の UDT を格納して領域を無駄にすることはありません。 この NULL に関するチェックは CLR から UDT が渡されるたびに実行されます。つまり、[!INCLUDE[tsql](../../includes/tsql-md.md)] の IS NULL コンストラクトを使用して NULL UDT のチェックを実行すると、必ず成功することを意味します。 **IsNull**プロパティは、インスタンスが null であるかどうかをテストするためにサーバーによっても使用されます。 UDT が NULL であることを判断できれば、サーバーはネイティブの NULL 処理を使用できます。  
  
 **IsNull**の**get()** メソッドは、特別な大文字と小文字を使用しません。 **ポイント**変数**\@p**が**Null**の場合**\@、p.IsNull**は、既定では"1"ではなく"NULL"と評価されます。 これは **、IsNull get()** メソッドの**SqlMethod(OnNullCall)** 属性がデフォルトで false になるためです。 オブジェクトは**Null**であるため、プロパティが要求されると、オブジェクトは逆シリアル化されず、メソッドは呼び出されず、既定値の "NULL" が返されます。  
  
### <a name="example"></a>例  
 次の例では、プライベート変数の `is_Null` に、UDT のインスタンスが NULL かどうかに関する状態が格納されます。 コードを作成する際は、`is_Null` の値を適切な状態に保つように注意する必要があります。 UDT には、UDT の null 値インスタンスを返す**Null**という名前の静的プロパティも必要です。 これにより、データベース内の UDT のインスタンスが実際に NULL の場合に、UDT から NULL 値を返すことができます。  
  
```vb  
Private is_Null As Boolean  
  
Public ReadOnly Property IsNull() As Boolean _  
   Implements INullable.IsNull  
    Get  
        Return (is_Null)  
    End Get  
End Property  
  
Public Shared ReadOnly Property Null() As Point  
    Get  
        Dim pt As New Point  
        pt.is_Null = True  
        Return (pt)  
    End Get  
End Property  
```  
  
```csharp  
private bool is_Null;  
  
public bool IsNull  
{  
    get  
    {  
        return (is_Null);  
    }  
}  
  
public static Point Null  
{  
    get  
    {  
        Point pt = new Point();  
        pt.is_Null = true;  
        return pt;  
    }  
}  
```  
  
### <a name="is-null-vs-isnull"></a>IS NULL と IsNull  
 ポイントが CLR UDT であるスキーマ Points (id int、位置ポイント) と次のクエリを含むテーブルを考えてみます。 **Point**  
  
```  
--Query 1  
SELECT ID  
FROM Points  
WHERE NOT (location IS NULL) -- Or, WHERE location IS NOT NULL;  
```  
  
```  
--Query 2:  
SELECT ID  
FROM Points  
WHERE location.IsNull = 0;  
```  
  
 どちらのクエリも **、NULL**以外の位置を持つポイントの ID を返します。 クエリ 1 では、通常の Null 処理が使用されるため、UDT のシリアル化解除は必要ありません。 一方、クエリ 2 では **、Null 以外**の各オブジェクトを逆シリアル化し **、ISNull**プロパティの値を取得するために CLR を呼び出す必要があります。 明らかに **、IS NULL を**使用するとパフォーマンスが向上し、コードから[!INCLUDE[tsql](../../includes/tsql-md.md)]UDT の**IsNull**プロパティを読み取る理由が決してありません。  
  
 では **、IsNull**プロパティの使用は何ですか? まず、CLR コード内から値が**Null**かどうかを判断する必要があります。 次に、サーバーはインスタンスが**Null であるかどうかを**テストする方法を必要とするため、このプロパティはサーバーによって使用されます。 **Null**であると判断した後、ネイティブの NULL 処理を使用して処理できます。  
  
## <a name="implementing-the-parse-method"></a>Parse メソッドの実装  
 **解析**メソッドと**ToString**メソッドを使用すると、UDT の文字列形式との間の変換が可能になります。 **Parse**メソッドを使用すると、文字列を UDT に変換できます。 静的 **(または**Visual Basic では**共有**) として宣言し、型のパラメーターを受け取る必要**があります**。  
  
 次のコードは、X 座標と Y 座標を分離する**Point** UDT の**Parse**メソッドを実装しています。 **Parse**メソッドには **、型**の引数が 1 つあり、X 値と Y 値がコンマ区切り文字列として指定されていると仮定します。 **属性を** **false**に設定すると、**解析**メソッドがポイントの null インスタンスから呼び出されるのを防ぎます。  
  
```vb  
<SqlMethod(OnNullCall:=False)> _  
Public Shared Function Parse(ByVal s As SqlString) As Point  
    If s.IsNull Then  
        Return Null  
    End If  
  
    ' Parse input string here to separate out points.  
    Dim pt As New Point()  
    Dim xy() As String = s.Value.Split(",".ToCharArray())  
    pt.X = Int32.Parse(xy(0))  
    pt.Y = Int32.Parse(xy(1))  
    Return pt  
End Function  
```  
  
```csharp  
[SqlMethod(OnNullCall = false)]  
public static Point Parse(SqlString s)  
{  
    if (s.IsNull)  
        return Null;  
  
    // Parse input string to separate out points.  
    Point pt = new Point();  
    string[] xy = s.Value.Split(",".ToCharArray());  
    pt.X = Int32.Parse(xy[0]);  
    pt.Y = Int32.Parse(xy[1]);  
    return pt;  
}  
```  
  
## <a name="implementing-the-tostring-method"></a>ToString メソッドの実装  
 **ToString**メソッドは、**ポイント**UDT を文字列値に変換します。 この場合 **、Point**型の Null インスタンスに対して文字列 "NULL" が返されます。 **ToString**メソッドは、X 座標と Y 座標値で構成されるコンマ区切りの**System.String**を返すために**System.Text.StringBuilder**を使用して**Parse**メソッドを逆にします。 **既定**では false であるため、**ポイント**の null インスタンスのチェックは不要です。  
  
```vb  
Private _x As Int32  
Private _y As Int32  
  
Public Overrides Function ToString() As String  
    If Me.IsNull Then  
        Return "NULL"  
    Else  
        Dim builder As StringBuilder = New StringBuilder  
        builder.Append(_x)  
        builder.Append(",")  
        builder.Append(_y)  
        Return builder.ToString  
    End If  
End Function  
```  
  
```csharp  
private Int32 _x;  
private Int32 _y;  
  
public override string ToString()  
{  
    if (this.IsNull)  
        return "NULL";  
    else  
    {  
        StringBuilder builder = new StringBuilder();  
        builder.Append(_x);  
        builder.Append(",");  
        builder.Append(_y);  
        return builder.ToString();  
    }  
}  
```  
  
## <a name="exposing-udt-properties"></a>UDT プロパティの公開  
 **Point** UDT は、**型 System.Int32**のパブリック読み取り/書き込みプロパティとして実装されている X 座標と Y 座標を公開します。  
  
```vb  
Public Property X() As Int32  
    Get  
        Return (Me._x)  
    End Get  
  
    Set(ByVal Value As Int32)  
        _x = Value  
    End Set  
End Property  
  
Public Property Y() As Int32  
    Get  
        Return (Me._y)  
    End Get  
  
    Set(ByVal Value As Int32)  
        _y = Value  
    End Set  
End Property  
```  
  
```csharp  
public Int32 X  
{  
    get  
    {  
        return this._x;  
    }  
    set   
    {  
        _x = value;  
    }  
}  
  
public Int32 Y  
{  
    get  
    {  
        return this._y;  
    }  
    set  
    {  
        _y = value;  
    }  
}  
```  
  
## <a name="validating-udt-values"></a>UDT 値の検証  
 UDT データの使用時は、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]により、バイナリ値が自動的に UDT 値に変換されます。 この変換処理では、値がその UDT のシリアル化形式に適しているかどうかがチェックされ、値を正しくシリアル化解除できるようにします。 これにより、値はバイナリ形式に再変換できるようになります。 また、バイト順の UDT の場合は、結果のバイナリ値が必ず元のバイナリ値と一致するようになります。 これにより、無効な値がデータベース内に存在する危険性が回避されます。 それでも、このレベルのチェックでは不十分である場合もあります。 UDT 値を一定の範囲内に制限する必要があるときは、さらに検証が必要になります。 たとえば、日付を実装する UDT の日の値は、特定の有効範囲内の正の数である必要があります。  
  
 プロパティ**の**プロパティ**を使用すると**、データが UDT に割り当てられたり UDT に変換されたときにサーバーが実行する検証メソッドの名前を指定できます。 検証**メソッド名**は、bcp ユーティリティ、一括挿入、DBCC CHECKDB、DBCC チェックファイルグループ、DBCC CHECKTABLE、分散クエリ、および表形式データ ストリーム (TDS) リモート プロシージャ コール (RPC) 操作の実行中にも呼び出されます。 **検証メソッド名**の既定値は null で、検証メソッドがないことを示します。  
  
### <a name="example"></a>例  
 次のコードは、検証**ポイントの検証メソッド名**を指定する**Point** **クラスの宣言**を示しています。  
  
```vb  
<Serializable(), SqlUserDefinedTypeAttribute(Format.Native, _  
  IsByteOrdered:=True, _  
  ValidationMethodName:="ValidatePoint")> _  
  Public Structure Point  
```  
  
```csharp  
[Serializable]  
[Microsoft.SqlServer.Server.SqlUserDefinedType(Format.Native,  
  IsByteOrdered=true,   
  ValidationMethodName = "ValidatePoint")]  
public struct Point : INullable  
{  
```  
  
 検証メソッドを指定する場合は、次のコードに示すようなシグネチャが必要です。  
  
```vb  
Private Function ValidationFunction() As Boolean  
    If (validation logic here) Then  
        Return True  
    Else  
        Return False  
    End If  
End Function  
```  
  
```csharp  
private bool ValidationFunction()  
{  
    if (validation logic here)  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
}  
```  
  
 検証メソッドは任意のスコープを持つことができるので、値が有効な場合は**true**を返し、それ以外の場合は**false を**返します。 メソッドが**false を**返すか、例外をスローした場合、値は無効として扱われ、エラーが発生します。  
  
 次のコード例では、0 以上の値のみが X 座標および Y 座標として許可されます。  
  
```vb  
Private Function ValidatePoint() As Boolean  
    If (_x >= 0) And (_y >= 0) Then  
        Return True  
    Else  
        Return False  
    End If  
End Function  
```  
  
```csharp  
private bool ValidatePoint()  
{  
    if ((_x >= 0) && (_y >= 0))  
    {  
        return true;  
    }  
    else  
    {  
        return false;  
    }  
}  
```  
  
### <a name="validation-method-limitations"></a>検証メソッドの制限事項  
 サーバーから検証メソッドが呼び出されるのは、サーバーで変換が実行されるときです。個別のプロパティを設定したり [!INCLUDE[tsql](../../includes/tsql-md.md)] INSERT ステートメントを使用してデータを挿入するときには呼び出されません。  
  
 検証メソッドをすべての状況で実行する場合は、プロパティセッターと**Parse**メソッドから検証メソッドを明示的に呼び出す必要があります。 この呼び出しは必須ではなく、場合によっては不適切な呼び出しになることもあります。  
  
### <a name="parse-validation-example"></a>Parse による検証の例  
 **ValidatePoint**メソッドが**Point**クラスで呼び出されるようにするには **、Parse**メソッドと、X 座標値と Y 座標値を設定するプロパティ プロシージャから呼び出す必要があります。 次のコードは **、Parse**関数から**ValidatePoint**検証メソッドを呼び出す方法を示しています。  
  
```vb  
<SqlMethod(OnNullCall:=False)> _  
Public Shared Function Parse(ByVal s As SqlString) As Point  
    If s.IsNull Then  
        Return Null  
    End If  
  
    ' Parse input string here to separate out points.  
    Dim pt As New Point()  
    Dim xy() As String = s.Value.Split(",".ToCharArray())  
    pt.X = Int32.Parse(xy(0))  
    pt.Y = Int32.Parse(xy(1))  
  
    ' Call ValidatePoint to enforce validation  
    ' for string conversions.  
    If Not pt.ValidatePoint() Then  
        Throw New ArgumentException("Invalid XY coordinate values.")  
    End If  
    Return pt  
End Function  
```  
  
```csharp  
[SqlMethod(OnNullCall = false)]  
public static Point Parse(SqlString s)  
{  
    if (s.IsNull)  
        return Null;  
  
    // Parse input string to separate out points.  
    Point pt = new Point();  
    string[] xy = s.Value.Split(",".ToCharArray());  
    pt.X = Int32.Parse(xy[0]);  
    pt.Y = Int32.Parse(xy[1]);  
  
    // Call ValidatePoint to enforce validation  
    // for string conversions.  
    if (!pt.ValidatePoint())   
        throw new ArgumentException("Invalid XY coordinate values.");  
    return pt;  
}  
```  
  
### <a name="property-validation-example"></a>Property による検証の例  
 次のコードは、X 座標と Y 座標を設定するプロパティ プロシージャから**ValidatePoint**検証メソッドを呼び出す方法を示しています。  
  
```vb  
Public Property X() As Int32  
    Get  
        Return (Me._x)  
    End Get  
  
    Set(ByVal Value As Int32)  
        Dim temp As Int32 = _x  
        _x = Value  
        If Not ValidatePoint() Then  
            _x = temp  
            Throw New ArgumentException("Invalid X coordinate value.")  
        End If  
    End Set  
End Property  
  
Public Property Y() As Int32  
    Get  
        Return (Me._y)  
    End Get  
  
    Set(ByVal Value As Int32)  
        Dim temp As Int32 = _y  
        _y = Value  
        If Not ValidatePoint() Then  
            _y = temp  
            Throw New ArgumentException("Invalid Y coordinate value.")  
        End If  
    End Set  
End Property  
```  
  
```csharp  
    public Int32 X  
{  
    get  
    {  
        return this._x;  
    }  
    // Call ValidatePoint to ensure valid range of Point values.  
    set   
    {  
        Int32 temp = _x;  
        _x = value;  
        if (!ValidatePoint())  
        {  
            _x = temp;  
            throw new ArgumentException("Invalid X coordinate value.");  
        }  
    }  
}  
  
public Int32 Y  
{  
    get  
    {  
        return this._y;  
    }  
    set  
    {  
        Int32 temp = _y;  
        _y = value;  
        if (!ValidatePoint())  
        {  
            _y = temp;  
            throw new ArgumentException("Invalid Y coordinate value.");  
        }  
    }  
}  
```  
  
## <a name="coding-udt-methods"></a>UDT メソッドのコーディング  
 UDT メソッドをコーディングする際は、使用するアルゴリズムが時間の経過と共に変化する可能性があるかどうかを考慮します。 変化する可能性がある場合は、UDT で使用するメソッド用に独立したクラスを作成することを検討します。 アルゴリズムが変化したら、新しいコードになったクラスを再コンパイルし、UDT に影響を与えることなくそのアセンブリを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に読み込むことができます。 多くの場合、UDT は [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY ステートメントを使用して再読み込みできますが、既存のデータとの間に問題が発生する可能性があります。 たとえば **、AdventureWorks**サンプル データベースに含まれる**通貨**UDT は **、変換関数**を使用して、別のクラスに実装されている通貨値を変換します。 変換アルゴリズムが今後どう変化するかは予測できず、新しい機能が必要になる可能性もあります。 **変換関数**を**通貨**UDT 実装から分離すると、将来の変更を計画する際の柔軟性が向上します。  
  
### <a name="example"></a>例  
 **ポイント**クラスには、**距離、距離****の From、** および**距離 FromXY**という 3 つの簡単な方法があります。 各関数は、**点**から 0 までの距離、指定した点から**点**までの距離、および指定した X 座標と Y 座標から点までの距離を**計算する倍精度**浮動小数点**数**を返します。 **Distance**と**Distance 各**呼び出し**から DistanceFromXY**を呼び出し、各メソッドに対して異なる引数を使用する方法を示します。  
  
```vb  
' Distance from 0 to Point.  
<SqlMethod(OnNullCall:=False)> _  
Public Function Distance() As Double  
    Return DistanceFromXY(0, 0)  
End Function  
  
' Distance from Point to the specified point.  
<SqlMethod(OnNullCall:=False)> _  
Public Function DistanceFrom(ByVal pFrom As Point) As Double  
    Return DistanceFromXY(pFrom.X, pFrom.Y)  
End Function  
  
' Distance from Point to the specified x and y values.  
<SqlMethod(OnNullCall:=False)> _  
Public Function DistanceFromXY(ByVal ix As Int32, ByVal iy As Int32) _  
    As Double  
    Return Math.Sqrt(Math.Pow(ix - _x, 2.0) + Math.Pow(iy - _y, 2.0))  
End Function  
```  
  
```csharp  
// Distance from 0 to Point.  
[SqlMethod(OnNullCall = false)]  
public Double Distance()  
{  
    return DistanceFromXY(0, 0);  
}  
  
// Distance from Point to the specified point.  
[SqlMethod(OnNullCall = false)]  
public Double DistanceFrom(Point pFrom)  
{  
    return DistanceFromXY(pFrom.X, pFrom.Y);  
}  
  
// Distance from Point to the specified x and y values.  
[SqlMethod(OnNullCall = false)]  
public Double DistanceFromXY(Int32 iX, Int32 iY)  
{  
    return Math.Sqrt(Math.Pow(iX - _x, 2.0) + Math.Pow(iY - _y, 2.0));  
}  
```  
  
### <a name="using-sqlmethod-attributes"></a>SqlMethod 属性の使用  
 クラス**は**、決定論を指定したり、null 呼び出し動作を指定したり、メソッドがミューターかどうかを指定したりするために、メソッド定義をマークするために使用できるカスタム属性を提供します。 これらのプロパティは既定値に設定されるので、既定値以外の値を設定する場合のみカスタム属性を使用します。  
  
> [!NOTE]  
>  クラス**は**クラスから継承するため、**TableDefinition****クラスは、SqlFunctionAttribute**から**フィールドを継承**します。 **SqlFunctionAttribute** **SqlFunctionAttribute** これは、一見テーブル値メソッドを記述できることを示していますが、この場合には該当しません。 メソッドがコンパイルされ、アセンブリが配置されますが、実行時に**IEnumerable**戻り値の型に関するエラーが発生し、"アセンブリ '\<\<\<アセンブリ ' アセンブリ ' アセンブリ '>' のクラス ' クラス '> ' のメソッド、プロパティ、またはフィールド ' 名前>' が無効な戻り型です。  
  
 次の表では、UDT メソッドで使用できる関連する**Microsoft.SqlServer.Server.SqlMethodAttribute**プロパティの一部を説明し、既定値を一覧表示します。  
  
 DataAccess  
 関数から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスに格納されているユーザー データにアクセスする必要があるかどうかを示します。 既定値は**データアクセスの種類です**。**なし**.  
  
 IsDeterministic  
 入力値とデータベースの状態が同じであれば、関数から同じ値が出力されるかどうかを示します。 既定値は **false**です。  
  
 IsMutator  
 メソッドにより UDT インスタンスの状態が変化するかどうかを示します。 既定値は **false**です。  
  
 IsPrecise  
 浮動小数点演算など、厳密な結果が算出されない計算が関数に含まれているかどうかを示します。 既定値は **false**です。  
  
 OnNullCall  
 入力引数に NULL 参照が指定されたときにメソッドが呼び出されるかどうかを示します。 デフォルトは**true です**。  
  
### <a name="example"></a>例  
 プロパティ**を**使用すると、UDT のインスタンスの状態を変更できるメソッドをマークできます。 [!INCLUDE[tsql](../../includes/tsql-md.md)] では、1 つの UPDATE ステートメントの SET 句に 2 つの UDT プロパティを設定できません。 ただし、2 つのメンバーを変更するミューテーターとしてメソッドをマークすることはできます。  
  
> [!NOTE]  
>  ミューテーター メソッドはクエリ内では使用できません。 代入ステートメントかデータ変更ステートメントでのみ、これらのメソッドを呼び出すことができます。 ミュータとしてマークされたメソッドが**void**を返さない場合 (または Visual Basic の**Sub**ではない場合)、CREATE TYPE はエラーで失敗します。  
  
 次のステートメントは **、Rotate**メソッドを持つ**三角形**UDT が存在することを前提としています。 次[!INCLUDE[tsql](../../includes/tsql-md.md)]の update ステートメントは **、Rotate**メソッドを呼び出します。  
  
```  
UPDATE Triangles SET t.RotateY(0.6) WHERE id=5  
```  
  
 **Rotate**メソッドは、メソッドをミュータメソッドとしてマーク[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]できるように **、IsMutator**を**true**に設定する**SqlMethod**属性で修飾されます。 また、入力パラメーターのいずれかが null 参照の場合に、メソッドが null 参照 (Visual Basic では**何も)** を返さないることをサーバーに示す**OnNullCall**を**false**に設定します。  
  
```vb  
<SqlMethod(IsMutator:=True, OnNullCall:=False)> _  
Public Sub Rotate(ByVal anglex as Double, _  
  ByVal angley as Double, ByVal anglez As Double)   
   RotateX(anglex)  
   RotateY(angley)  
   RotateZ(anglez)  
End Sub  
```  
  
```csharp  
[SqlMethod(IsMutator = true, OnNullCall = false)]  
public void Rotate(double anglex, double angley, double anglez)   
{  
   RotateX(anglex);  
   RotateY(angley);  
   RotateZ(anglez);  
}  
```  
  
## <a name="implementing-a-udt-with-a-user-defined-format"></a>ユーザー定義形式による UDT の実装  
 ユーザー定義形式で UDT を実装する場合は、UDT データのシリアル化と逆シリアル化を処理するインターフェイスを実装する**読み取り**および**書き込み**メソッドを実装する必要があります。 プロパティを指定する必要**MaxByteSize****もあります。**  
  
### <a name="the-currency-udt"></a>Currency UDT  
 **通貨**UDT は、 で始まる CLR サンプル[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に含まれています[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]。  
  
 **通貨**UDT は、特定のカルチャの通貨システムにおける金額の処理をサポートします。 2 つのフィールドを定義する必要があります: **CultureInfo**の**文字列**は、通貨を発行したユーザー (en-us など) と**通貨値**の**10 進数**、金額の金額を指定します。  
  
 サーバーで比較を実行するために使用されるわけではありませんが、**通貨**UDT は**System.IComparable**インターフェイスを**実装しています。** このインターフェイスは、クライアント側でカルチャ内の通貨値を正しく比較したり並べ替えたりする場合に使用されます。  
  
 CLR で実行されているコードでは、カルチャが通貨値とは別に比較されます。 [!INCLUDE[tsql](../../includes/tsql-md.md)] コードでは、次の操作により比較結果が決まります。  
  
1.  **IsByteOrdered**属性を true に設定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]し、比較のためにディスク上の永続化バイナリ表現を使用するように指示します。  
  
2.  **Currency** UDT の**Write**メソッドを使用して、ディスク上で UDT がどのように永続化されているか、および操作のために UDT[!INCLUDE[tsql](../../includes/tsql-md.md)]値がどのように比較および順序付けされているかを判断します。  
  
3.  次のバイナリ形式を使用して**通貨**UDT を保存します。  

    1.  0 バイト目から 19 バイト目までは UTF-16 エンコードされた文字列としてカルチャを保存します。右側の不足バイトには NULL 文字が埋め込まれます。  
  
    2.  20 バイト目以降を使用して、通貨の 10 進値を保存します。  
  
 NULL 文字を埋め込む目的は、カルチャと通貨値を完全に分離することです。これにより、[!INCLUDE[tsql](../../includes/tsql-md.md)] コードで UDT が比較されるとき、カルチャ バイトどうし、通貨バイト値どうしが比較されるようになります。  
  
 **通貨**UDT の完全なコードリストについては、「 [SQL Server データベース エンジンのサンプル](https://msftengprodsamples.codeplex.com/)」の CLR サンプルのインストール手順に従ってください。  
  
### <a name="currency-attributes"></a>Currency の属性  
 **通貨**UDT は、次の属性で定義されます。  
  
```vb  
<Serializable(), Microsoft.SqlServer.Server.SqlUserDefinedType( _  
    Microsoft.SqlServer.Server.Format.UserDefined, _  
    IsByteOrdered:=True, MaxByteSize:=32), _  
    CLSCompliant(False)> _  
Public Structure Currency  
Implements INullable, IComparable, _  
Microsoft.SqlServer.Server.IBinarySerialize  
```  
  
```csharp  
[Serializable]  
[SqlUserDefinedType(Format.UserDefined,   
    IsByteOrdered = true, MaxByteSize = 32)]  
    [CLSCompliant(false)]  
    public struct Currency : INullable, IComparable, IBinarySerialize  
    {  
```  
  
## <a name="creating-read-and-write-methods-with-ibinaryserialize"></a>IBinarySerialize を備えた Read メソッドと Write メソッドの作成  
 **ユーザー定義**のシリアル化形式を選択する場合は **、IBinarySerialize**インターフェイスを実装し、独自の**読み取り**および**書き込み**メソッドを作成する必要があります。 **通貨**UDT の次の手順では **、システム.IO.バイナリリーダー**と**システム.IO.BinaryWriter**を使用して、UDT の読み取りと書き込みを行います。  
  
```vb  
' IBinarySerialize methods  
' The binary layout is as follow:  
'    Bytes 0 - 19: Culture name, padded to the right with null  
'    characters, UTF-16 encoded  
'    Bytes 20+: Decimal value of money  
' If the culture name is empty, the currency is null.  
Public Sub Write(ByVal w As System.IO.BinaryWriter) _  
  Implements Microsoft.SqlServer.Server.IBinarySerialize.Write  
    If Me.IsNull Then  
        w.Write(nullMarker)  
        w.Write(System.Convert.ToDecimal(0))  
        Return  
    End If  
  
    If cultureName.Length > cultureNameMaxSize Then  
        Throw New ApplicationException(String.Format(CultureInfo.CurrentUICulture, _  
           "{0} is an invalid culture name for currency as it is too long.", cultureNameMaxSize))  
    End If  
  
    Dim paddedName As String = cultureName.PadRight(cultureNameMaxSize, CChar(vbNullChar))  
  
    For i As Integer = 0 To cultureNameMaxSize - 1  
        w.Write(paddedName(i))  
    Next i  
  
    ' Normalize decimal value to two places  
    currencyVal = Decimal.Floor(currencyVal * 100) / 100  
    w.Write(currencyVal)  
End Sub  
  
Public Sub Read(ByVal r As System.IO.BinaryReader) _  
  Implements Microsoft.SqlServer.Server.IBinarySerialize.Read  
    Dim name As Char() = r.ReadChars(cultureNameMaxSize)  
    Dim stringEnd As Integer = Array.IndexOf(name, CChar(vbNullChar))  
  
    If stringEnd = 0 Then  
        cultureName = Nothing  
        Return  
    End If  
  
    cultureName = New String(name, 0, stringEnd)  
    currencyVal = r.ReadDecimal()  
End Sub  
  
```  
  
```csharp  
// IBinarySerialize methods  
// The binary layout is as follow:  
//    Bytes 0 - 19:Culture name, padded to the right   
//    with null characters, UTF-16 encoded  
//    Bytes 20+:Decimal value of money  
// If the culture name is empty, the currency is null.  
public void Write(System.IO.BinaryWriter w)  
{  
    if (this.IsNull)  
    {  
        w.Write(nullMarker);  
        w.Write((decimal)0);  
        return;  
    }  
  
    if (cultureName.Length > cultureNameMaxSize)  
    {  
        throw new ApplicationException(string.Format(  
            CultureInfo.InvariantCulture,   
            "{0} is an invalid culture name for currency as it is too long.",   
            cultureNameMaxSize));  
    }  
  
    String paddedName = cultureName.PadRight(cultureNameMaxSize, '\0');  
    for (int i = 0; i < cultureNameMaxSize; i++)  
    {  
        w.Write(paddedName[i]);  
    }  
  
    // Normalize decimal value to two places  
    currencyValue = Decimal.Floor(currencyValue * 100) / 100;  
    w.Write(currencyValue);  
}  
public void Read(System.IO.BinaryReader r)  
{  
    char[] name = r.ReadChars(cultureNameMaxSize);  
    int stringEnd = Array.IndexOf(name, '\0');  
  
    if (stringEnd == 0)  
    {  
        cultureName = null;  
        return;  
    }  
  
    cultureName = new String(name, 0, stringEnd);  
    currencyValue = r.ReadDecimal();  
}  
```  
  
 **通貨**UDT の完全なコードリストについては、「 [SQL Server データベース エンジンのサンプル](https://msftengprodsamples.codeplex.com/)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [ユーザー定義型を作成する](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
