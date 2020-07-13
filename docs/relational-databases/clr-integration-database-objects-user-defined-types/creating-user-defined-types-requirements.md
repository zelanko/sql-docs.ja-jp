---
title: ユーザー定義型の要件 |Microsoft Docs
description: この記事では、SQL Server にインストールする UDT を作成するときに行う必要がある、設計上の重要な決定事項について説明します。
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- UDTs [CLR integration], requirements
- serialization
- Native serialization format [CLR integration]
- attributes [CLR integration]
- XML serialization [CLR integration]
- user-defined types [CLR integration], requirements
- user-defined serialization [CLR integration]
- user-defined types [CLR integration], Native serialization
- UDTs [CLR integration], Native serialization
ms.assetid: bedc3372-50eb-40f2-bcf2-d6db6a63b7e6
author: rothja
ms.author: jroth
ms.openlocfilehash: b20192a3804dfba713b04706d528738ceb8768c3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727809"
---
# <a name="creating-user-defined-types---requirements"></a>ユーザー定義型の作成 - 要件
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  にインストールするユーザー定義型 (UDT) を作成する際には、いくつかの重要な設計上の決定を行う必要があり [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。 ほとんどの場合は、UDT を構造体として作成することをお勧めしますが、クラスとして作成することもできます。 UDT の定義は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に登録する UDT を作成するための仕様に準拠している必要があります。  
  
## <a name="requirements-for-implementing-udts"></a>UDT の実装要件  
 UDT を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で実行するには、UDT の定義に次の要件を実装する必要があります。  
  
 UDT は**SqlUserDefinedTypeAttribute**を指定する必要があります。 **SerializableAttribute**の使用は省略可能ですが、推奨されます。  
  
-   UDT は、public **static** (Visual Basic) Null メソッド**を作成**することによって、クラスまたは構造体に**INullable**インターフェイスを実装する必要があり [!INCLUDE[msCoName](../../includes/msconame-md.md)] ます。 **Null** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、既定で NULL 値に対応します。 この作業は、UDT で実行されるコードが NULL 値を認識するために必要です。  
  
-   UDT には、からの解析をサポートするパブリックな**static** (または**Shared**) **Parse**メソッドと、オブジェクトの文字列形式に変換するためのパブリック**ToString**メソッドが含まれている必要があります。  
  
-   ユーザー定義のシリアル化形式を持つ UDT は、system.string **serialize**インターフェイスを実装し、 **Read**および**Write**メソッドを提供する必要があります。  
  
-   UDT はSystem.Xml を実装する必要があり**ます。XmlIgnore は、標準**のシリアル化をオーバーライドする必要がある場合に、XML シリアル化可能な型であるか、またはすべてのパブリックフィールドとプロパティが**XmlIgnore**属性で修飾されている必要があります。  
  
-   UDT オブジェクトのシリアル化は 1 つだけ存在する必要があります。 シリアル化ルーチンまたはシリアル化解除ルーチンでは、特定のオブジェクトの表現が複数認識されると検証が失敗します。  
  
-   **SqlUserDefinedTypeAttribute.IsByteOrdered** must be **true** to compare data in byte order. IComparable インターフェイスが実装されておらず、 **SqlUserDefinedTypeAttribute**が**false**である場合、バイト順の比較は失敗します。  
  
-   クラスで定義する UDT には、引数を受け取らないバプリック コンストラクターを含める必要があります。 必要に応じて、オーバーロードのクラス コンストラクターを追加作成できます。  
  
-   UDT では、データ要素をパブリック フィールドまたはプロパティ プロシージャとして公開する必要があります。  
  
-   パブリック名は、128文字より長くすることはできません [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。また、[データベース識別子](../../relational-databases/databases/database-identifiers.md)で定義されている識別子の名前付け規則に従っている必要があります。  
  
-   **sql_variant**列に UDT のインスタンスを含めることはできません。  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] の型システムでは UDT 間の継承階層に対応していないので、継承されたメンバーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からアクセスすることはできません。 ただし、型のマネージド コード実装では、継承を使用してクラスを構造化したり、そのクラスのメソッドを呼び出すことができます。  
  
-   クラス コンストラクター以外のメンバーはオーバーロードできません。 オーバーロード メソッドを作成した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にアセンブリを登録したり、型を作成するときにはエラーは発生しません。 オーバーロード メソッドが検出されるのは、型の作成時ではなく実行時です。 オーバーロード メソッドは、呼び出されない限りクラス内に存在することができます。 エラーは、オーバーロード メソッドを呼び出した時点で発生します。  
  
-   **Static** (または**Shared**) メンバーはすべて、定数として、または読み取り専用として宣言する必要があります。 静的メンバーを変更可能にすることはできません。  
  
-   **SqlUserDefinedTypeAttribute**フィールドが-1 に設定されている場合、シリアル化された UDT は、ラージオブジェクト (LOB) のサイズの上限 (現在 2 GB) と同じ大きさになることがあります。 UDT のサイズは、 **Maxbytesized**よって認識されるフィールドに指定された値を超えることはできません。  
  
> [!NOTE]  
>  比較を実行するためにサーバーによって使用されることはありませんが、必要に応じて、1つのメソッドである**CompareTo**を公開する**system.icomparable**インターフェイスを実装することができます。 このインターフェイスは、クライアント側で UDT 値を正確に比較したり並べ替える場合に使用します。  
  
## <a name="native-serialization"></a>ネイティブ シリアル化  
 UDT に適したシリアル化属性は、作成する UDT の種類によって異なります。 **ネイティブ**シリアル化形式では、非常に単純な構造を使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がディスク上に UDT の効率的なネイティブ表現を格納できるようにします。 UDT が単純で、次の型のフィールドのみが含まれている場合は、**ネイティブ**形式をお勧めします。  
  
 **bool**、 **byte**、 **sbyte**、 **short**、 **ushort**、 **int**、 **uint**、 **long**、 **ulong**、 **float**、 **double**、 **sqlbyte**、 **SqlInt16**、 **SqlInt32**、 **SqlInt64**、 **sqlbyte**、 **sqlbyte**、 **sqlbyte**、 **sqlbyte**、 **sqlbyte**  
  
 上記の型のフィールドで構成される値型は、Visual C# の**構造体**、(Visual Basic で認識されている**構造体**など) の**ネイティブ**形式に適しています。 たとえば、**ネイティブ**シリアル化形式で指定された udt には、**ネイティブ**形式でも指定された別の udt のフィールドが含まれている場合があります。 UDT 定義がより複雑で、上記の一覧にないデータ型が含まれている場合は **、代わりに**ユーザー定義のシリアル化形式を指定する必要があります。  
  
 **ネイティブ**形式には、次の要件があります。  
  
-   この型では、 **SqlUserDefinedTypeAttribute**の値を指定できないようにする必要があります。  
  
-   すべてのフィールドがシリアル化可能である必要があります。  
  
-   UDT が構造体ではなくクラスで定義されている場合は、 **StructLayoutAttribute**を**StructLayout**として指定する必要があります。 この属性は、データ フィールドの物理レイアウトを制御し、メンバーを出現順にレイアウトするために使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、この属性を使用して複数の値を持つ UDT のフィールド順序を決定します。  
  
 **ネイティブ**シリアル化を使用して定義された udt の例については、[ユーザー定義型のコーディング](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md)の Point udt に関する記述を参照してください。  
  
## <a name="userdefined-serialization"></a>ユーザー定義シリアル化  
 **SqlUserDefinedTypeAttribute**属性の [指定可能な形式] 設定を使用**すると、** 開発者はバイナリ形式を完全に制御できます。 "**書式**属性" プロパティを [ユーザー設定] として指定する場合**は、コード**で次の操作を行う必要があります。  
  
-   省略可能な**Isbyteordered**属性プロパティを指定します。 既定値は **false** です。  
  
-   **SqlUserDefinedTypeAttribute**の**maxbytesize**プロパティを指定します。  
  
-   System.string **serialize**インターフェイスを実装することによって、UDT の**読み取り**および**書き込み**メソッドを実装するコードを記述します。  
  
 ユーザー定義のシリアル化を使用して定義さ**れた udt**の例については、「[ユーザー定義型のコーディング](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md)における通貨 udt」を参照してください。  
  
> [!NOTE]  
>  UDT フィールドをインデックス化するには、ネイティブ シリアル化を使用するか、UDT フィールドを保存する必要があります。  
  
## <a name="serialization-attributes"></a>シリアル化属性  
 UDT のストレージ表現を構築し、クライアントに UDT を値として転送するためにシリアル化を使用する方法は、属性で決まります。 UDT を作成するときは、 **SqlUserDefinedTypeAttribute**を指定する必要があります。 **SqlUserDefinedTypeAttribute**属性は、クラスが udt であることを示し、udt のストレージを指定します。 必要に応じて、 **Serializable**属性を指定することもできますが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] これは必須ではありません。  
  
 **SqlUserDefinedTypeAttribute**には、次のプロパティがあります。  
  
 **Format**  
 UDT のデータ型に応じて、**ネイティブ**また**は**独自に設定できるシリアル化形式を指定します。  
  
 **IsByteOrdered**  
 **Boolean** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が UDT でバイナリ比較を実行する方法を決定するブール値。  
  
 **IsFixedLength**  
 この UDT のすべてのインスタンスの長さが同じであるかどうかを示します。  
  
 **MaxByteSize**  
 インスタンスのバイト単位の最大サイズ。 ユーザー設定**のシリアル化形式で** **maxbytesize**指定する必要があります。 ユーザー定義のシリアル化を指定した UDT の場合、 **Maxbytesize** 、ユーザーが定義したように、シリアル化された形式の udt の合計サイズを参照します。 **Maxbytesize**値は、1 ~ 8000 の範囲で指定する必要があります。または、UDT が8000バイトより大きいことを示すには-1 に設定する必要があります (合計サイズが LOB の最大サイズを超えることはできません)。 文字列のプロパティが 10**文字 (system.string**) の UDT を考えてみます。 BinaryWriter を使用して UDT をシリアル化すると、シリアル化された文字列の合計サイズは 22 バイトになります。このサイズは、2 バイト (Unicode UTF-16 の文字 1 文字) に最大文字数を掛け、さらにバイナリ ストリームのシリアル化から生じるオーバーヘッドの制御バイト 2 バイトを加えたものです。 したがって、 **Maxbytesize**値を決定する場合は、シリアル化された UDT の合計サイズを考慮する必要があります。これは、バイナリ形式でシリアル化されるデータのサイズと、シリアル化によって発生するオーバーヘッドを加算したものです。  
  
 **ValidationMethodName**  
 UDT のインスタンスの検証に使用するメソッドの名前。  
  
### <a name="setting-isbyteordered"></a>IsByteOrdered の設定  
 **SqlUserDefinedTypeAttribute**プロパティが**true**に設定されている場合は、シリアル化されたバイナリデータを使用して情報を意味のある順序で並べ替えることができます。 したがって、バイト順の UDT オブジェクトの各インスタンスは、シリアル化された表現を 1 つだけ持つことができます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でシリアル化されたバイト列の比較操作を行うときは、その比較結果がマネージド コードで同じ比較操作を実行した場合と同じになる必要があります。 **Isbyteordered**が**true**に設定されている場合も、次の機能がサポートされます。  
  
-   この型の列にインデックスを作成する機能。  
  
-   この型の列に CHECK 制約と UNIQUE 制約だけでなく主キーと外部キーを作成する機能。  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] の ORDER BY 句、GROUP BY 句、および PARTITION BY 句を使用する機能。 これらの句を使用した場合、順序の決定には型のバイナリ表現が使用されます。  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで比較演算子を使用する機能。  
  
-   この型の計算列を保存する機能。  
  
 **Isbyteordered**が**true**に設定さ**れている**場合、**ネイティブ**シリアル化形式と対象設定の両方のシリアル化形式で次の比較演算子がサポートされることに注意してください。  
  
-   等しい (=)  
  
-   等しくない (!=)  
  
-   より大きい (>)  
  
-   より小さい (\<)  
  
-   以上 (>=)  
  
-   以下 (<=)  
  
### <a name="implementing-nullability"></a>NULL 値の許容属性の実装  
 アセンブリの属性を正しく指定することに加えて、クラスで NULL 値の許容属性をサポートする必要があります。 に読み込ま [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] れる udt は null 対応ですが、udt が null 値を認識できるようにするには、クラスで**INullable**インターフェイスを実装する必要があります。 UDT に null 値の許容属性を実装する方法の詳細と例については、「[ユーザー定義型のコーディング](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md)」を参照してください。  
  
### <a name="string-conversions"></a>文字列の変換  
 UDT との間の文字列変換をサポートするには、クラスで**Parse**メソッドと**ToString**メソッドを指定する必要があります。 **Parse**メソッドを使用すると、文字列を UDT に変換できます。 これは、 **static**として宣言されている (または Visual Basic で**共有**されている) 必要があり、 **SqlString**型のパラメーターを受け取ります。 **Parse**メソッドと**ToString**メソッドを実装する方法の詳細と例については、「[ユーザー定義型のコーディング](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md)」を参照してください。  
  
## <a name="xml-serialization"></a>XML シリアル化  
 Udt は、XML シリアル化のコントラクトに準拠して、 **xml**データ型との間の変換をサポートする必要があります。 **System.Xml。シリアル化**名前空間には、オブジェクトを XML 形式のドキュメントまたはストリームにシリアル化するために使用されるクラスが含まれています。 Xml**シリアル化の実装は**、xml シリアル化と逆シリアル化のカスタム書式設定を提供する**IXmlSerializable**インターフェイスを使用して行うことができます。  
  
 Xml シリアル化を使用すると、UDT から**xml**への明示的な変換に加えて、次のことが可能になります。  
  
-   **Xml**データ型に変換した後、UDT インスタンスの値に対して**Xquery**を使用します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のネイティブ XML Web サービスにより、パラメーター化クエリと Web メソッドに UDT を使用できます。  
  
-   UDT を使用して、XML データの一括読み込みを受け取ることができます。  
  
-   UDT 列を含むテーブルが格納されたデータセットをシリアル化できます。  
  
 UDT は、FOR XML クエリではシリアル化されません。 Udt の XML シリアル化を表示する FOR XML クエリを実行するには、各 UDT 列を SELECT ステートメントの**xml**データ型に明示的に変換します。 また、列を**varbinary**、 **varchar**、または**nvarchar**に明示的に変換することもできます。  
  
## <a name="see-also"></a>関連項目  
 [ユーザー定義型を作成する](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
