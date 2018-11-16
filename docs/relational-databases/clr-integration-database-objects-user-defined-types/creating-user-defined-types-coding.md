---
title: ユーザー定義型のコーディング |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: b3e8921e230f581f60c96e6443d4fa5b71a417b3
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51661562"
---
# <a name="creating-user-defined-types---coding"></a>ユーザー定義型の作成 - コーディング
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  ユーザー定義型 (UDT) の定義をコーディングする際は、形式やシリアル化のオプションを選択するだけでなく、UDT をクラスと構造体のどちらで実装するかによって、さまざまな機能を実装する必要があります。  
  
 例では、このセクションでは、実装を示します、**ポイント**としての UDT を**構造体**(または**構造**Visual Basic で)。 **ポイント**UDT は X と Y 座標としてが実装されています。 プロパティ プロシージャ。  
  
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
  
 **Microsoft.SqlServer.Server**名前空間には、UDT のさまざまな属性に必要なオブジェクトが含まれていますと**System.Data.SqlTypes**名前空間には、を表すクラスが含まれています[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。アセンブリに使用できるネイティブ データ型。 それ以外にもアセンブリが正しく機能するために必要な名前空間が存在する場合があります。 **ポイント**UDT を使用しても、 **System.Text**文字列を操作するための名前空間。  
  
> [!NOTE]  
>  Visual C のデータベース オブジェクト、Udt を使用してコンパイルなど **/clr: 純粋な**実行はサポートされていません。  
  
## <a name="specifying-attributes"></a>属性の指定  
 UDT のストレージ表現を構築し、クライアントに UDT を値として転送するためにシリアル化を使用する方法は、属性で決まります。  
  
 **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**が必要です。 **Serializable**属性は省略可能です。 指定することも、 **Microsoft.SqlServer.Server.SqlFacetAttribute** UDT の戻り値の型に関する情報を提供します。 詳細については、「[CLR ルーチンのカスタム属性](../../relational-databases/clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md)」を参照してください。  
  
### <a name="point-udt-attributes"></a>Point UDT の属性  
 **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**のストレージ形式を設定、**ポイント**に UDT**ネイティブ**します。 **IsByteOrdered**に設定されている**true**、ことの比較結果が同じ SQL Server で同じ比較は、マネージ コードで配置を実行した場合とを保証します。 UDT の実装、 **System.Data.SqlTypes.INullable** UDT の null を対応するインターフェイス。  
  
 次のコード フラグメントの属性を示しています、**ポイント**UDT します。  
  
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
 アセンブリの属性を正しく指定することに加えて、UDT で NULL 値の許容属性をサポートする必要があります。 読み込まれる Udt[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は null に対応して、UDT に null 値を認識させるためには、UDT を実装する必要がありますが、 **System.Data.SqlTypes.INullable**インターフェイス。  
  
 という名前のプロパティを作成する必要があります**IsNull**値が CLR コード内から null かどうかを判断するのに必要な。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では UDT が NULL インスタンスであることを検出すると、通常の NULL 値処理メソッドを使用して UDT を保存します。 そのため、サーバーが NULL の UDT の不要なシリアル化やシリアル化解除に時間を費やしたり、NULL の UDT を格納して領域を無駄にすることはありません。 この NULL に関するチェックは CLR から UDT が渡されるたびに実行されます。つまり、[!INCLUDE[tsql](../../includes/tsql-md.md)] の IS NULL コンストラクトを使用して NULL UDT のチェックを実行すると、必ず成功することを意味します。 **IsNull**プロパティは、インスタンスが null かどうかをテストするサーバーでも使用されます。 UDT が NULL であることを判断できれば、サーバーはネイティブの NULL 処理を使用できます。  
  
 **Get()** メソッドの**IsNull**何らかの方法で特殊なケースではありません。 場合、**ポイント**変数**@p**は**Null**、し**@p.IsNull**既定では、"NULL"を評価「1」です。 これは、ため、 **SqlMethod(OnNullCall)** の属性、 **IsNull get()** メソッド既定値は false。 オブジェクトは**Null**プロパティが要求されると、オブジェクトが逆シリアル化できません、メソッドが呼び出されないと既定値は"NULL"が返されます。  
  
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
 スキーマ ポイント (id int, location Point) を格納するテーブルについて考えてみます**ポイント**は CLR UDT の場合は、次のクエリ。  
  
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
  
 両方のクエリがポイント以外の Id を返す**Null**場所。 クエリ 1 では、通常の Null 処理が使用されるため、UDT のシリアル化解除は必要ありません。 クエリ 2 は、その一方で、各以外を逆シリアル化が**Null**オブジェクトし、の値を取得する CLR への呼び出し、 **IsNull**プロパティ。 明らかを使用して**IS NULL**パフォーマンスが向上し、詳細を読む理由しないで、 **IsNull**プロパティから UDT の[!INCLUDE[tsql](../../includes/tsql-md.md)]コード。  
  
 そのため、新機能の使用、 **IsNull**プロパティか? 値がかどうかを判断する必要がある最初に、 **Null** CLR コード内から。 サーバー インスタンスがあるかどうかをテストする方法を必要な第 2 に、 **Null**ので、このプロパティは、サーバーによって使用されます。 判別した後は**Null**、ネイティブの null 処理がそれを処理するために使用できます。  
  
## <a name="implementing-the-parse-method"></a>Parse メソッドの実装  
 **解析**と**ToString**メソッドを使用して、UDT の文字列表現の間の変換をします。 **解析**メソッドにより UDT に変換する文字列。 として宣言する必要がある必要があります**静的**(または**Shared** Visual basic)、型のパラメーターを受け取ると**System.Data.SqlTypes.SqlString**します。  
  
 次のコードで実装、**解析**のメソッド、**ポイント**UDT で、X および Y 座標は、切り離されます。 **解析**メソッドが型の 1 つの引数**System.Data.SqlTypes.SqlString**X と Y の値がコンマ区切りの文字列として指定されたことを前提としています。 設定、 **Microsoft.SqlServer.Server.SqlMethodAttribute.OnNullCall**属性を**false**により、**解析**からの null インスタンスから呼び出されるメソッドポイント。  
  
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
 **ToString**メソッドに変換、**ポイント**UDT を文字列値にします。 ここでは、文字列"NULL"が返されますの Null インスタンスを**ポイント**型。 **ToString**メソッド反転、**解析**メソッドを使用して、 **System.Text.StringBuilder**をコンマ区切りを返す**System.String**X と Y 座標の値で構成されます。 **InvokeIfReceiverIsNull**既定値は false のインスタンスの null チェック**ポイント**必要はありません。  
  
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
 **ポイント**UDT 型のパブリックの読み取り/書き込みプロパティとして実装される X および Y 座標を公開する**System.Int32**します。  
  
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
  
 **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute.ValidationMethodName**のプロパティ、 **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**名前を指定することができますときに、サーバーを実行する検証メソッドのデータが UDT に割り当てるか、UDT に変換します。 **ValidationMethodName** bcp ユーティリティ、BULK INSERT、DBCC CHECKDB、DBCC CHECKFILEGROUP、DBCC CHECKTABLE、分散クエリ、および表形式データ ストリーム (TDS) リモート プロシージャ コール (RPC) 操作の実行中とも呼ばれます。 既定値**ValidationMethodName**が null の場合、検証メソッドがないことを示します。  
  
### <a name="example"></a>例  
 次のコード フラグメントの宣言を示しています、**ポイント**を指定するには、クラス、 **ValidationMethodName**の**ValidatePoint**します。  
  
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
  
 検証メソッドが任意のスコープを持つことができ、返す必要があります**true**値が、有効な場合と**false**それ以外の場合。 メソッドを返す場合**false**または例外をスローするには、値として処理が有効でないとエラーが発生します。  
  
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
  
 プロパティ set アクセス操作子から検証メソッドを明示的に呼び出す必要があります、**解析**メソッド検証メソッドをすべての状況で実行する場合。 この呼び出しは必須ではなく、場合によっては不適切な呼び出しになることもあります。  
  
### <a name="parse-validation-example"></a>Parse による検証の例  
 いることを確認する、 **ValidatePoint**でメソッドが呼び出される、**ポイント**クラスを呼び出す必要があることから、**解析**メソッドと、X と Y を設定するプロパティ プロシージャから値を調整します。 次のコード フラグメントを呼び出す方法を示しています、 **ValidatePoint**から検証メソッド、**解析**関数。  
  
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
 次のコード フラグメントを呼び出す方法を示しています、 **ValidatePoint** X および Y 座標を設定するプロパティ プロシージャから検証メソッド。  
  
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
 UDT メソッドをコーディングする際は、使用するアルゴリズムが時間の経過と共に変化する可能性があるかどうかを考慮します。 変化する可能性がある場合は、UDT で使用するメソッド用に独立したクラスを作成することを検討します。 アルゴリズムが変化したら、新しいコードになったクラスを再コンパイルし、UDT に影響を与えることなくそのアセンブリを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に読み込むことができます。 多くの場合、UDT は [!INCLUDE[tsql](../../includes/tsql-md.md)] ALTER ASSEMBLY ステートメントを使用して再読み込みできますが、既存のデータとの間に問題が発生する可能性があります。 たとえば、**通貨**UDT に含まれる、 **AdventureWorks**サンプル データベースの使用、 **ConvertCurrency**は実装されている通貨値を変換する関数別のクラス。 変換アルゴリズムが今後どう変化するかは予測できず、新しい機能が必要になる可能性もあります。 分離、 **ConvertCurrency**関数を**通貨**将来の変更を計画するときに、UDT の実装によって柔軟性が向上します。  
  
### <a name="example"></a>例  
 **ポイント**クラスには、距離を計算するための 3 つの単純なメソッドが含まれています:**距離**、 **DistanceFrom**と**DistanceFromXY**します。 返します、**二重**からの距離を計算する**ポイント**を 0 に指定したポイントからの距離に**ポイント**からの距離は、X および Y 座標を指定**ポイント**します。 **距離**と**DistanceFrom**の各呼び出し**DistanceFromXY**、メソッドごとに異なる引数を使用する方法を示します。  
  
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
 **Microsoft.SqlServer.Server.SqlMethodAttribute**クラスにメソッドがミューテーターであるかどうかを指定して、null 呼び出しの動作、決定性を指定するには、メソッドの定義のマークに使用できるカスタム属性が用意されています。 これらのプロパティは既定値に設定されるので、既定値以外の値を設定する場合のみカスタム属性を使用します。  
  
> [!NOTE]  
>  **SqlMethodAttribute**クラスから継承、 **SqlFunctionAttribute**ためクラス**SqlMethodAttribute**継承、 **FillRowMethodName**と**TableDefinition**からフィールド**SqlFunctionAttribute**します。 これは、一見テーブル値メソッドを記述できることを示していますが、この場合には該当しません。 メソッドをコンパイルし、アセンブリ展開すると、エラーについて、 **IEnumerable**返す型は、次のメッセージの実行時に発生します:"メソッド、プロパティ、またはフィールド '\<名 >' クラスで\<クラス>' のアセンブリで '\<アセンブリ >' が無効な戻り値の型"。  
  
 次の表では、いくつかの関連について説明します**Microsoft.SqlServer.Server.SqlMethodAttribute** UDT のメソッドで使用でき、その既定値を一覧表示するプロパティ。  
  
 DataAccess  
 関数から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスに格納されているユーザー データにアクセスする必要があるかどうかを示します。 既定値は**DataAccessKind**.**None**します。  
  
 IsDeterministic  
 入力値とデータベースの状態が同じであれば、関数から同じ値が出力されるかどうかを示します。 既定値は**false**します。  
  
 IsMutator  
 メソッドにより UDT インスタンスの状態が変化するかどうかを示します。 既定値は**false**します。  
  
 IsPrecise  
 浮動小数点演算など、厳密な結果が算出されない計算が関数に含まれているかどうかを示します。 既定値は**false**します。  
  
 OnNullCall  
 入力引数に NULL 参照が指定されたときにメソッドが呼び出されるかどうかを示します。 既定値は**true**します。  
  
### <a name="example"></a>例  
 **Microsoft.SqlServer.Server.SqlMethodAttribute.IsMutator**プロパティでは、UDT のインスタンスの状態の変化を許可するメソッドをマークすることができます。 [!INCLUDE[tsql](../../includes/tsql-md.md)] では、1 つの UPDATE ステートメントの SET 句に 2 つの UDT プロパティを設定できません。 ただし、2 つのメンバーを変更するミューテーターとしてメソッドをマークすることはできます。  
  
> [!NOTE]  
>  ミューテーター メソッドはクエリ内では使用できません。 代入ステートメントかデータ変更ステートメントでのみ、これらのメソッドを呼び出すことができます。 メソッドは、ミューテーターを返さないようマークされている場合**void** (または、 **Sub** Visual Basic で)、CREATE TYPE はエラーで失敗します。  
  
 次のステートメントの存在を前提としています、**三角形**を持つ UDT、**回転**メソッド。 次[!INCLUDE[tsql](../../includes/tsql-md.md)]update ステートメントで呼び出される、**回転**メソッド。  
  
```  
UPDATE Triangles SET t.RotateY(0.6) WHERE id=5  
```  
  
 **回転**でメソッドを装飾、 **SqlMethod**属性設定**IsMutator**に**true**ように[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]マークを付けることができますミューテーター メソッドとしてメソッド。 コードにも設定**OnNullCall**に**false**、メソッドが null 参照を返しますでサーバーを示します (**Nothing** Visual Basic で) 場合は、入力のいずれかパラメーターは、null 参照です。  
  
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
 実装する必要があるユーザー定義の書式を持つ UDT を実装するときに**読み取り**と**書き込み**をシリアル化を処理する Microsoft.SqlServer.Server.IBinarySerialize インターフェイスを実装するメソッドとUDT データを逆シリアル化します。 指定する必要があります、 **MaxByteSize**のプロパティ、 **Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**します。  
  
### <a name="the-currency-udt"></a>Currency UDT  
 **通貨**UDT のと共にインストールできる CLR サンプルに含まれている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]以降[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]します。  
  
 **通貨**UDT は、特定のカルチャの通貨システムでの金額の処理をサポートしています。 2 つのフィールドを定義する必要があります。**文字列**の**CultureInfo**、通貨の発行元を指定します (en-など) と**10 進**の**CurrencyValue**money の量。  
  
 比較を実行するため、サーバーで使用されていませんが、**通貨**UDT の実装、 **System.IComparable**インターフェイスで、1 つのメソッドを公開するには、 **System.IComparable.CompareTo**します。 このインターフェイスは、クライアント側でカルチャ内の通貨値を正しく比較したり並べ替えたりする場合に使用されます。  
  
 CLR で実行されているコードでは、カルチャが通貨値とは別に比較されます。 [!INCLUDE[tsql](../../includes/tsql-md.md)] コードでは、次の操作により比較結果が決まります。  
  
1.  設定、 **IsByteOrdered**属性が true で、通知に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]比較のディスクで永続化されたバイナリ表現を使用します。  
  
2.  使用して、**書き込み**のメソッド、**通貨**UDT を永続化する方法を決定する UDT ディスクとそのため UDT 値を比較し、順序付ける方法[!INCLUDE[tsql](../../includes/tsql-md.md)]操作。  
  
3.  保存、**通貨**次のバイナリ形式を使用して UDT:  
  
    1.  0 バイト目から 19 バイト目までは UTF-16 エンコードされた文字列としてカルチャを保存します。右側の不足バイトには NULL 文字が埋め込まれます。  
  
    2.  20 バイト目以降を使用して、通貨の 10 進値を保存します。  
  
 NULL 文字を埋め込む目的は、カルチャと通貨値を完全に分離することです。これにより、[!INCLUDE[tsql](../../includes/tsql-md.md)] コードで UDT が比較されるとき、カルチャ バイトどうし、通貨バイト値どうしが比較されるようになります。  
  
 完全なコードのリスト、**通貨**UDT サンプルの CLR をインストールするための手順に従います[SQL Server データベース エンジン サンプル](https://msftengprodsamples.codeplex.com/)します。  
  
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
 選択すると**UserDefined**シリアル化形式を実装することも必要があります、 **IBinarySerialize**インターフェイスを独自に作成**読み取り**と**書き込み**メソッド。 次の手順を**通貨**UDT の使用、 **System.IO.BinaryReader**と**System.IO.BinaryWriter**に読み取りし、書き込みを行います。  
  
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
  
 完全なコードのリスト、**通貨**UDT を参照してください[SQL Server データベース エンジン サンプル](https://msftengprodsamples.codeplex.com/)します。  
  
## <a name="see-also"></a>参照  
 [ユーザー定義型を作成する](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
