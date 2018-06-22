---
title: ユーザー定義型のコーディング |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: reference
ms.tgt_pltfrm: ''
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
caps.latest.revision: 37
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b3a698c63fa5fc7e5a0802716b3112df31cf241f
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35697903"
---
# <a name="creating-user-defined-types---coding"></a>ユーザー定義型のコーディングを作成します。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  ユーザー定義型 (UDT) の定義をコーディングする際は、形式やシリアル化のオプションを選択するだけでなく、UDT をクラスと構造体のどちらで実装するかによって、さまざまな機能を実装する必要があります。  
  
 このセクションの例では、実装を示しています。、**ポイント**として UDT、**構造体**(または**構造**Visual Basic で)。 **ポイント**UDT は X と Y 座標として実装されているプロパティ プロシージャです。  
  
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
  
 **Microsoft.SqlServer.Server**名前空間には、UDT のさまざまな属性に必要なオブジェクトが含まれています、 **System.Data.SqlTypes**名前空間には、を表すクラスが含まれています[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。アセンブリに使用できるネイティブ データ型。 それ以外にもアセンブリが正しく機能するために必要な名前空間が存在する場合があります。 **ポイント**UDT を使用しても、 **System.Text**文字列の操作を名前空間。  
  
> [!NOTE]  
>  Visual C のデータベース オブジェクト、コンパイルした Udt など **/clr: 純粋な**実行はサポートされていません。  
  
## <a name="specifying-attributes"></a>属性の指定  
 UDT のストレージ表現を構築し、クライアントに UDT を値として転送するためにシリアル化を使用する方法は、属性で決まります。  
  
 **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**が必要です。 **Serializable**属性は省略可能です。 指定することも、 **Microsoft.SqlServer.Server.SqlFacetAttribute** UDT の戻り値の型に関する情報を提供します。 詳細については、「[CLR ルーチンのカスタム属性](../../relational-databases/clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md)」を参照してください。  
  
### <a name="point-udt-attributes"></a>Point UDT の属性  
 **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**のストレージ形式を設定、**ポイント**に UDT**ネイティブ**です。 **IsByteOrdered**に設定されている**true**比較の結果が異なる SQL Server のように行われた場合、同じ比較したマネージ コードですることを保証します。 UDT を実装して、 **System.Data.SqlTypes.INullable** UDT の null を対応するインターフェイスです。  
  
 次のコード フラグメントの属性を示しています、**ポイント**UDT です。  
  
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
 アセンブリの属性を正しく指定することに加えて、UDT で NULL 値の許容属性をサポートする必要があります。 読み込まれる Udt[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は null に対応する、UDT に null 値を認識するためには、UDT を実装する必要がありますが、 **System.Data.SqlTypes.INullable**インターフェイスです。  
  
 という名前のプロパティを作成する必要があります**IsNull**値が CLR コード内から null かどうかを判断するに必要なです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では UDT が NULL インスタンスであることを検出すると、通常の NULL 値処理メソッドを使用して UDT を保存します。 そのため、サーバーが NULL の UDT の不要なシリアル化やシリアル化解除に時間を費やしたり、NULL の UDT を格納して領域を無駄にすることはありません。 この NULL に関するチェックは CLR から UDT が渡されるたびに実行されます。つまり、[!INCLUDE[tsql](../../includes/tsql-md.md)] の IS NULL コンストラクトを使用して NULL UDT のチェックを実行すると、必ず成功することを意味します。 **IsNull**プロパティにも使用によって、サーバー インスタンスが null かどうかをテストします。 UDT が NULL であることを判断できれば、サーバーはネイティブの NULL 処理を使用できます。  
  
 **Get()** メソッドの**IsNull**任意の方法で、特殊な例ではありません。 場合、**ポイント**変数**@p**は**Null**、し**@p.IsNull**が、既定と評価される"NULL"、「1」です。 これは、ため、 **SqlMethod(OnNullCall)** の属性、 **IsNull get()** メソッド既定値は false。 このオブジェクトは**Null**オブジェクトが逆シリアル化されない、メソッドが呼び出されないと、既定値は"NULL"が返されるプロパティが要求されたときに、します。  
  
### <a name="example"></a>例  
 次の例では、プライベート変数の `is_Null` に、UDT のインスタンスが NULL かどうかに関する状態が格納されます。 コードを作成する際は、`is_Null` の値を適切な状態に保つように注意する必要があります。 UDT はという名前の静的プロパティにも必要**Null** UDT の null 値のインスタンスを返します。 これにより、データベース内の UDT のインスタンスが実際に NULL の場合に、UDT から NULL 値を返すことができます。  
  
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
 ここでスキーマ ポイント (id int, 場所ポイント) を格納するテーブルについて考えてみます**ポイント**CLR UDT、および次のクエリには。  
  
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
  
 両方のクエリはポイント以外の Id を返す**Null**場所。 クエリ 1 では、通常の Null 処理が使用されるため、UDT のシリアル化解除は必要ありません。 クエリ 2 はその一方で、各非を逆シリアル化が**Null**オブジェクトし、CLR での値を取得するに呼び出せる、 **IsNull**プロパティです。 を使用する**IS NULL**パフォーマンスが向上し、接続しないで読み取らなければならない理由、 **IsNull**から UDT のプロパティ[!INCLUDE[tsql](../../includes/tsql-md.md)]コード。  
  
 、、の使用、 **IsNull**プロパティしますか? 値があるかどうかを判断する必要がある最初に、 **Null** CLR コード内からです。 サーバー インスタンスがあるかどうかをテストする方法を必要な第二に、 **Null**ので、このプロパティは、サーバーによって使用されます。 判断した後は**Null**、そのネイティブの null 処理を使用してそれを処理することができます。  
  
## <a name="implementing-the-parse-method"></a>Parse メソッドの実装  
 **解析**と**ToString**メソッドを使用して、UDT の文字列形式から変換します。 **解析**メソッドにより UDT に変換する文字列。 として宣言されなければなりません**静的**(または**Shared** Visual Basic で)、型のパラメーターを受け取ると**System.Data.SqlTypes.SqlString**です。  
  
 次のコードを実装して、**解析**のメソッド、**ポイント**UDT で、X および Y 座標を分離します。 **解析**メソッドが型の単一の引数を持つ**System.Data.SqlTypes.SqlString**X と Y の値がコンマ区切りの文字列として指定されたことを前提としています。 設定、 **Microsoft.SqlServer.Server.SqlMethodAttribute.OnNullCall**属性を**false**により、**解析**からの null インスタンスから呼び出されるメソッドポイントです。  
  
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
 **ToString**メソッドに変換、**ポイント**UDT を文字列値にします。 Null インスタンスに文字列"NULL"が返されます、ここで、**ポイント**型です。 **ToString**メソッド反転、**解析**メソッドを使用して、 **System.Text.StringBuilder**をコンマで区切られたを返す**System.String**X と Y 座標の値で構成されます。 **InvokeIfReceiverIsNull**既定値は false、確認の null インスタンスを**ポイント**必要はありません。  
  
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
 **ポイント**UDT 型のパブリックの読み取り/書き込みプロパティとして実装される X と Y 座標を公開する**System.Int32**です。  
  
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
 UDT データの使用時は、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]により、バイナリ値が自動的に UDT 値に変換されます。 この変換処理では、値がその UDT のシリアル化形式に適しているかどうかがチェックされ、値を正しくシリアル化解除できるようにします。 これにより、値をバイナリ形式に変換できること。 また、バイト順の UDT の場合は、結果のバイナリ値が必ず元のバイナリ値と一致するようになります。 これにより、無効な値がデータベース内に存在する危険性が回避されます。 それでも、このレベルのチェックでは不十分である場合もあります。 UDT 値を一定の範囲内に制限する必要があるときは、さらに検証が必要になります。 たとえば、日付を実装する UDT の日の値は、特定の有効範囲内の正の数である必要があります。  
  
 **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.ValidationMethodName**のプロパティ、 **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**名前を指定することができますサーバーが実行時に検証メソッドのデータが、UDT に割り当てられているか、UDT に変換されます。 **ValidationMethodName** bcp ユーティリティ、BULK INSERT、DBCC CHECKDB、DBCC CHECKFILEGROUP、DBCC CHECKTABLE、分散クエリ、および表形式データ ストリーム (TDS) リモート プロシージャ コール (RPC) 操作の実行中にも呼び出されます。 既定値**ValidationMethodName**が null の場合、検証メソッドがないことを示すです。  
  
### <a name="example"></a>例  
 次のコード フラグメントの宣言を示しています、**ポイント**を指定するには、クラス、 **ValidationMethodName**の**ValidatePoint**です。  
  
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
  
 検証メソッドが任意のスコープを持つことができ、返す必要があります**true**値が、有効な場合と**false**それ以外の場合。 メソッドを返す場合**false**または例外をスローするには、値扱われます。 有効ではありませんし、エラーが発生します。  
  
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
  
 プロパティ set アクセス操作子から、検証メソッドを明示的に呼び出す必要があります、**解析**メソッド検証メソッドをすべての状況で実行する場合。 この呼び出しは必須ではなく、場合によっては不適切な呼び出しになることもあります。  
  
### <a name="parse-validation-example"></a>Parse による検証の例  
 いることを確認する、 **ValidatePoint**でメソッドが呼び出される、**ポイント**クラスを呼び出す必要がありますから、**解析**メソッドと、X と Y を設定するプロパティ プロシージャから値を調整します。 次のコード フラグメントを呼び出す方法を示します、 **ValidatePoint**検証方法を**解析**関数。  
  
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
 次のコード フラグメントを呼び出す方法を示します、 **ValidatePoint** X 座標と Y 座標を設定するプロパティ プロシージャからメソッドを検証します。  
  
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
 UDT メソッドをコーディングする際は、使用するアルゴリズムが時間の経過と共に変化する可能性があるかどうかを考慮します。 変化する可能性がある場合は、UDT で使用するメソッド用に独立したクラスを作成することを検討します。 アルゴリズムが変化したら、新しいコードになったクラスを再コンパイルし、UDT に影響を与えることなくそのアセンブリを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に読み込むことができます。 多くの場合、UDT は [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY ステートメントを使用して再読み込みできますが、既存のデータとの間に問題が発生する可能性があります。 たとえば、**通貨**に UDT が含まれている、 **AdventureWorks**サンプル データベースは、 **ConvertCurrency**は実装されている通貨値を変換する関数別のクラスです。 変換アルゴリズムが今後どう変化するかは予測できず、新しい機能が必要になる可能性もあります。 分離、 **ConvertCurrency**から機能、**通貨**将来の変更を計画するときに、UDT の実装によって高い柔軟性が実現します。  
  
### <a name="example"></a>例  
 **ポイント**クラスには、距離を計算するための 3 つの単純なメソッドが含まれています:**距離**、 **DistanceFrom**と**DistanceFromXY**です。 返します、**二重**からの距離を計算する**ポイント**には、0 を指定した点からの距離**ポイント**からの距離は、X 座標と Y 座標を指定**ポイント**です。 **距離**と**DistanceFrom**の各呼び出し**DistanceFromXY**、し、各メソッドの異なる引数を使用する方法を示します。  
  
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
 **Microsoft.SqlServer.Server.SqlMethodAttribute**クラスが null の呼び出しの動作の決定性を指定するために、メソッドがミューテーター メソッドがあるかどうかを指定するメソッドの定義を示すために使用できるカスタム属性を提供します。 これらのプロパティは既定値に設定されるので、既定値以外の値を設定する場合のみカスタム属性を使用します。  
  
> [!NOTE]  
>  **SqlMethodAttribute**クラスから継承、 **SqlFunctionAttribute**クラス、そのため**SqlMethodAttribute**継承、 **FillRowMethodName**と**TableDefinition**からのフィールド**SqlFunctionAttribute**です。 これは、一見テーブル値メソッドを記述できることを示していますが、この場合には該当しません。 メソッドをコンパイルし、アセンブリ展開すると、エラーについて、 **IEnumerable**実行時に、次のメッセージで発生する型を返す:"メソッド、プロパティ、またはフィールド '\<名 >' クラスで\<クラス>' のアセンブリで '\<アセンブリ >' が無効な戻り値の型です"。  
  
 次の表の関連**Microsoft.SqlServer.Server.SqlMethodAttribute**プロパティを UDT メソッドで使用でき、既定値を一覧表示します。  
  
 DataAccess  
 関数から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスに格納されているユーザー データにアクセスする必要があるかどうかを示します。 既定値は**DataAccessKind**.**None**です。  
  
 IsDeterministic  
 入力値とデータベースの状態が同じであれば、関数から同じ値が出力されるかどうかを示します。 既定値は**false**です。  
  
 IsMutator  
 メソッドにより UDT インスタンスの状態が変化するかどうかを示します。 既定値は**false**です。  
  
 IsPrecise  
 浮動小数点演算など、厳密な結果が算出されない計算が関数に含まれているかどうかを示します。 既定値は**false**です。  
  
 OnNullCall  
 入力引数に NULL 参照が指定されたときにメソッドが呼び出されるかどうかを示します。 既定値は**true**です。  
  
### <a name="example"></a>例  
 **Microsoft.SqlServer.Server.SqlMethodAttribute.IsMutator**プロパティでは、UDT のインスタンスの状態の変化を許可するメソッドをマークすることができます。 [!INCLUDE[tsql](../../includes/tsql-md.md)] では、1 つの UPDATE ステートメントの SET 句に 2 つの UDT プロパティを設定できません。 ただし、2 つのメンバーを変更するミューテーターとしてメソッドをマークすることはできます。  
  
> [!NOTE]  
>  ミューテーター メソッドはクエリ内では使用できません。 代入ステートメントかデータ変更ステートメントでのみ、これらのメソッドを呼び出すことができます。 メソッドは、ミューテーターを返さないとしてマークされている場合**void** (または、 **Sub** Visual Basic で)、CREATE TYPE はエラーで失敗します。  
  
 次のステートメントを想定しています、**三角形**UDT が、**回転**メソッドです。 次[!INCLUDE[tsql](../../includes/tsql-md.md)]update ステートメントが呼び出されて、**回転**メソッド。  
  
```  
UPDATE Triangles SET t.RotateY(0.6) WHERE id=5  
```  
  
 **回転**でメソッドを装飾、 **SqlMethod**属性設定**IsMutator**に**true**ように[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]マークを付けることができますミューテーター メソッドとしてメソッド。 コードにも設定**OnNullCall**に**false**、メソッドが null 参照を返すことで、サーバーを示します (**Nothing** Visual Basic で) 入力のいずれかパラメーターは、null 参照です。  
  
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
 ユーザー定義形式を持つ UDT を実装するときに実装する必要あります**読み取り**と**書き込み**をシリアル化を処理する Microsoft.SqlServer.Server.IBinarySerialize インターフェイスを実装するメソッドとUDT データを逆シリアル化します。 指定する必要があります、 **MaxByteSize**のプロパティ、 **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**です。  
  
### <a name="the-currency-udt"></a>Currency UDT  
 **通貨**UDT がと共にインストールできる CLR サンプルの値が含まれる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で始まる、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]です。  
  
 **通貨**UDT は、特定のカルチャの通貨システムでの金額の処理をサポートしています。 2 つのフィールドを定義する必要があります。**文字列**の**CultureInfo**、通貨の発行者を指定する (en-など) と**decimal**の**CurrencyValue**、金額です。  
  
 ない使用されますが、サーバーによって、比較を実行するため、**通貨**を実装し、 **System.IComparable**インターフェイスで、1 つのメソッドを公開するには、 **System.IComparable.CompareTo**です。 このインターフェイスは、クライアント側でカルチャ内の通貨値を正しく比較したり並べ替えたりする場合に使用されます。  
  
 CLR で実行されているコードでは、カルチャが通貨値とは別に比較されます。 [!INCLUDE[tsql](../../includes/tsql-md.md)] コードでは、次の操作により比較結果が決まります。  
  
1.  設定、 **IsByteOrdered**属性が true で、通知に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]比較にディスクに永続化されたバイナリ表現を使用します。  
  
2.  使用して、**書き込み**のメソッド、**通貨**UDT を永続化する方法を決定する UDT ディスクしたがって UDT 値を比較し、順序付ける方法[!INCLUDE[tsql](../../includes/tsql-md.md)]操作します。  
  
3.  保存、**通貨**次のバイナリ形式を使用して UDT を。  
  
    1.  0 バイト目から 19 バイト目までは UTF-16 エンコードされた文字列としてカルチャを保存します。右側の不足バイトには NULL 文字が埋め込まれます。  
  
    2.  20 バイト目以降を使用して、通貨の 10 進値を保存します。  
  
 NULL 文字を埋め込む目的は、カルチャと通貨値を完全に分離することです。これにより、[!INCLUDE[tsql](../../includes/tsql-md.md)] コードで UDT が比較されるとき、カルチャ バイトどうし、通貨バイト値どうしが比較されるようになります。  
  
 完全なコードの一覧を**通貨**UDT、サンプルの CLR をインストールするための手順に従ってください[SQL Server データベース エンジン サンプル](http://msftengprodsamples.codeplex.com/)です。  
  
### <a name="currency-attributes"></a>Currency の属性  
 **通貨**次属性を持つ UDT が定義されています。  
  
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
 選択すると**UserDefined**シリアル化形式を実装することも必要があります、 **IBinarySerialize**インターフェイスし、独自に作成**読み取り**と**書き込み**メソッドです。 次の手順、**通貨**UDT を使用して、 **System.IO.BinaryReader**と**System.IO.BinaryWriter**からの読み取りと書き込み、UDT にします。  
  
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
  
 完全なコードの一覧を**通貨**UDT を参照してください[SQL Server データベース エンジン サンプル](http://msftengprodsamples.codeplex.com/)です。  
  
## <a name="see-also"></a>参照  
 [ユーザー定義型を作成する](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
