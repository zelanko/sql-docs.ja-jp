---
title: ユーザー定義型の要件 |マイクロソフトドキュメント
description: この資料では、SQL Server にインストールする UDT を作成するときに必要な設計上の重要な決定事項について説明します。
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
ms.openlocfilehash: 2b19a9179cba2225a2209255ce48220669e4bbef
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81486971"
---
# <a name="creating-user-defined-types---requirements"></a>ユーザー定義型の作成 - 要件
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  にインストールするユーザー定義型 (UDT) を作成する場合は、いくつかの重要な設計[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]上の決定を行う必要があります。 ほとんどの場合は、UDT を構造体として作成することをお勧めしますが、クラスとして作成することもできます。 UDT の定義は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に登録する UDT を作成するための仕様に準拠している必要があります。  
  
## <a name="requirements-for-implementing-udts"></a>UDT の実装要件  
 UDT を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で実行するには、UDT の定義に次の要件を実装する必要があります。  
  
 UDT は、属性を指定**する**必要があります。 を使用する**場合**は省略可能ですが、推奨します。  
  
-   UDT は、パブリック**静的**( Visual Basic で**共有**) **Null**メソッドを作成することで、クラスまたは構造体に[!INCLUDE[msCoName](../../includes/msconame-md.md)]**System.Data.SqlTypes.INullable**インターフェイスを実装する必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、既定で NULL 値に対応します。 この作業は、UDT で実行されるコードが NULL 値を認識するために必要です。  
  
-   UDT には、解析をサポートするパブリック**静的** **(Shared)** **Parse**メソッドと、オブジェクトの文字列形式に変換するためのパブリック**ToString**メソッドが含まれている必要があります。  
  
-   ユーザー定義のシリアル化形式を持つ UDT は **、インターフェイス**を実装し、**読み取り**メソッドと**Write**メソッドを提供する必要があります。  
  
-   UDT は **、System.Xml.Serialization.IXmlSerializable**を実装する必要があります。 **XmlIgnore**  
  
-   UDT オブジェクトのシリアル化は 1 つだけ存在する必要があります。 シリアル化ルーチンまたはシリアル化解除ルーチンでは、特定のオブジェクトの表現が複数認識されると検証が失敗します。  
  
-   **SqlUserDefinedTypeAttribute.IsByteOrdered** must be **true** to compare data in byte order. インターフェイスが実装されておらず、**バイト順**の比較が**失敗**する場合。  
  
-   クラスで定義する UDT には、引数を受け取らないバプリック コンストラクターを含める必要があります。 必要に応じて、オーバーロードのクラス コンストラクターを追加作成できます。  
  
-   UDT では、データ要素をパブリック フィールドまたはプロパティ プロシージャとして公開する必要があります。  
  
-   パブリック名は 128 文字を超える必要があり、「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][データベース識別子](../../relational-databases/databases/database-identifiers.md)」で定義されている識別子の命名規則に従っている必要があります。  
  
-   **sql_variant**列に UDT のインスタンスを含めることはできません。  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] の型システムでは UDT 間の継承階層に対応していないので、継承されたメンバーに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からアクセスすることはできません。 ただし、型のマネージド コード実装では、継承を使用してクラスを構造化したり、そのクラスのメソッドを呼び出すことができます。  
  
-   クラス コンストラクター以外のメンバーはオーバーロードできません。 オーバーロード メソッドを作成した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にアセンブリを登録したり、型を作成するときにはエラーは発生しません。 オーバーロード メソッドが検出されるのは、型の作成時ではなく実行時です。 オーバーロード メソッドは、呼び出されない限りクラス内に存在することができます。 エラーは、オーバーロード メソッドを呼び出した時点で発生します。  
  
-   **静的** **(Shared)** メンバーは、定数として宣言するか、読み取り専用として宣言する必要があります。 静的メンバーを変更可能にすることはできません。  
  
-   **フィールド**が -1 に設定されている場合、シリアル化された UDT はラージ オブジェクト (LOB) サイズ制限 (現在は 2 GB) と同じ大きさになる可能性があります。 UDT のサイズは **、最大バイトサイズ**フィールドで指定された値を超えることはできません。  
  
> [!NOTE]  
>  サーバーで比較を実行するために使用されるわけではありませんが、オプションで単一のメソッド**を**公開する**System.IComparable**インターフェイスを実装できます。 このインターフェイスは、クライアント側で UDT 値を正確に比較したり並べ替える場合に使用します。  
  
## <a name="native-serialization"></a>ネイティブ シリアル化  
 UDT に適したシリアル化属性は、作成する UDT の種類によって異なります。 **ネイティブ**のシリアル化形式では、UDT の効率的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]なネイティブ表現をディスクに格納できる非常に単純な構造を使用します。 UDT が単純で、次の種類のフィールドのみが含まれている場合は、**ネイティブ**形式をお勧めします。  
  
 **ブール**,**バイト**, **sbyte**,**短い**, **ushort**, **int**, **uint**,**ロング**,**ウロン**,**浮動小数**,**ダブル**, **SqlByte**, **SqlInt16**, **SqlInt32**, **SqlInt64**, **SqlDateTime**, **SqlSingle**, **SqlDouble**, **SqlMoney**, **SqlBoolean**  
  
 上記の型のフィールドで構成される値型は、Visual C# の**構造体**(または Visual Basic で知られている**構造体**) などの**ネイティブ**形式の候補として適しています。 たとえば、**ネイティブ**シリアル化形式で指定された UDT には、**ネイティブ**形式で指定された別の UDT のフィールドが含まれている場合があります。 UDT 定義がより複雑で、上記の一覧にないデータ型が含まれている場合は、代わりに**UserDefined**シリアル化形式を指定する必要があります。  
  
 **ネイティブ**形式には、次の要件があります。  
  
-   この型は、値を指定してはな**りません。**  
  
-   すべてのフィールドがシリアル化可能である必要があります。  
  
-   UDT が構造体ではなくクラスで定義されている場合は **、構造体レイアウト.レイアウトKindSequential**として指定**する必要があります**。 この属性は、データ フィールドの物理レイアウトを制御し、メンバーを出現順にレイアウトするために使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、この属性を使用して複数の値を持つ UDT のフィールド順序を決定します。  
  
 **ネイティブ**シリアル化で定義された UDT の例については、「[ユーザー定義型のコーディング](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md)におけるポイント UDT 」を参照してください。  
  
## <a name="userdefined-serialization"></a>ユーザー定義シリアル化  
 **属性のユーザー定義**形式設定は**Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute**、開発者にバイナリ形式に対する完全な制御を提供します。 **Format**属性プロパティを**UserDefined**として指定する場合は、コードで次の操作を行う必要があります。  
  
-   オプションの**IsByteOrdered**属性プロパティを指定します。 既定値は **false** です。  
  
-   プロパティを**MaxByteSize**指定**します**。  
  
-   **インターフェイスを**実装して UDT の**読み取り**メソッドと**書き込み**メソッドを実装するコードを記述します。  
  
 **ユーザー定義**のシリアル化で定義された UDT の例については、「[ユーザー定義型のコーディング](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md)における通貨 UDT 」を参照してください。  
  
> [!NOTE]  
>  UDT フィールドをインデックス化するには、ネイティブ シリアル化を使用するか、UDT フィールドを保存する必要があります。  
  
## <a name="serialization-attributes"></a>シリアル化属性  
 UDT のストレージ表現を構築し、クライアントに UDT を値として転送するためにシリアル化を使用する方法は、属性で決まります。 UDT を作成するときには、属性を指定する必要**があります**。 属性**は**、クラスが UDT であることを示し、UDT のストレージを指定します。 必要に応じて **、シリアル化可能な**属性を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]指定できますが、この属性は必要ありません。  
  
 次**の**プロパティがあります。  
  
 **Format**  
 UDT のデータ型に応じて、シリアル化形式 (**ネイティブ**または**ユーザー定義**) を指定します。  
  
 **IsByteOrdered**  
 UDT でのバイナリ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]比較の実行方法を決定する**ブール**値。  
  
 **IsFixedLength**  
 この UDT のすべてのインスタンスの長さが同じであるかどうかを示します。  
  
 **MaxByteSize**  
 インスタンスのバイト単位の最大サイズ。 **ユーザー定義**のシリアル化形式で**MaxByteSize**を指定する必要があります。 ユーザー定義のシリアル化が指定された UDT の場合 **、MaxByteSize**は、ユーザーが定義したシリアル化形式での UDT の合計サイズを参照します。 **MaxByteSize**の値は 1 ~ 8000 の範囲内にするか、UDT が 8000 バイトを超えることを示すために -1 に設定する必要があります (合計サイズは最大 LOB サイズを超えることはできません)。 10 文字の文字列 (**System.Char**) のプロパティを持つ UDT を考えてみましょう。 BinaryWriter を使用して UDT をシリアル化すると、シリアル化された文字列の合計サイズは 22 バイトになります。このサイズは、2 バイト (Unicode UTF-16 の文字 1 文字) に最大文字数を掛け、さらにバイナリ ストリームのシリアル化から生じるオーバーヘッドの制御バイト 2 バイトを加えたものです。 したがって **、MaxByteSize**の値を決定する際には、シリアル化された UDT の合計サイズ (バイナリ形式でシリアル化されたデータのサイズと、シリアル化によって発生するオーバーヘッド) を考慮する必要があります。  
  
 **メソッド名を検証します。**  
 UDT のインスタンスの検証に使用するメソッドの名前。  
  
### <a name="setting-isbyteordered"></a>IsByteOrdered の設定  
 **プロパティが** **true**に設定されている場合、シリアル化されたバイナリ データを情報のセマンティック順序付けに使用できることを保証します。 したがって、バイト順の UDT オブジェクトの各インスタンスは、シリアル化された表現を 1 つだけ持つことができます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でシリアル化されたバイト列の比較操作を行うときは、その比較結果がマネージド コードで同じ比較操作を実行した場合と同じになる必要があります。 **IsByteOrdered**が**true**に設定されている場合は、次の機能もサポートされます。  
  
-   この型の列にインデックスを作成する機能。  
  
-   この型の列に CHECK 制約と UNIQUE 制約だけでなく主キーと外部キーを作成する機能。  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] の ORDER BY 句、GROUP BY 句、および PARTITION BY 句を使用する機能。 これらの句を使用した場合、順序の決定には型のバイナリ表現が使用されます。  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで比較演算子を使用する機能。  
  
-   この型の計算列を保存する機能。  
  
 **IsByteOrdered**が true に設定されている場合、**ネイティブ**シリアル化形式と**ユーザー定義**シリアル化形式の両方が、次の比較演算子をサポートすることに注意**してください**。  
  
-   等しい (=)  
  
-   等しくない (!=)  
  
-   より大きい (>)  
  
-   より小さい (\<)  
  
-   以上 (>=)  
  
-   以下 (<=)  
  
### <a name="implementing-nullability"></a>NULL 値の許容属性の実装  
 アセンブリの属性を正しく指定することに加えて、クラスで NULL 値の許容属性をサポートする必要があります。 にロードされる UDT[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は NULL を認識しますが、UDT が NULL 値を認識するためには、クラスが**INullable**インターフェイスを実装する必要があります。 UDT で NULL 値許容を実装する方法の詳細と例については、「[ユーザー定義型のコーディング](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md)」を参照してください。  
  
### <a name="string-conversions"></a>文字列の変換  
 UDT との文字列変換をサポートするには、クラスで**Parse**メソッドと**ToString**メソッドを指定する必要があります。 **Parse**メソッドを使用すると、文字列を UDT に変換できます。 静的 **(または**Visual Basic では**共有**) として宣言し、型のパラメーターを受け取る必要**があります**。 **Parse**メソッドと**ToString**メソッドの実装方法の詳細と例については、「[ユーザー定義型のコーディング](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types-coding.md)」を参照してください。  
  
## <a name="xml-serialization"></a>XML シリアル化  
 UDT は、XML シリアル化のコントラクトに準拠して **、xml**データ型との間の変換をサポートする必要があります。 **名前空間には、** オブジェクトを XML 形式のドキュメントまたはストリームにシリアル化するために使用されるクラスが含まれています。 XML シリアル化と逆シリアル化のカスタム書式を提供する**IXmlSerializable**インターフェイスを使用して **、xml**シリアル化を実装できます。  
  
 UDT から**xml**への明示的な変換を実行するだけでなく、XML シリアル化を使用すると、次のことが可能になります。  
  
-   **xml**データ型への変換後に UDT インスタンスの値に対して**Xquery**を使用します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のネイティブ XML Web サービスにより、パラメーター化クエリと Web メソッドに UDT を使用できます。  
  
-   UDT を使用して、XML データの一括読み込みを受け取ることができます。  
  
-   UDT 列を含むテーブルが格納されたデータセットをシリアル化できます。  
  
 UDT は、FOR XML クエリではシリアル化されません。 UDT の XML シリアル化を表示する FOR XML クエリを実行するには、各 UDT 列を SELECT ステートメントで**XML**データ型に明示的に変換します。 列を明示的に**varbinary**、 **varchar**、または**nvarchar**に明示的に変換することもできます。  
  
## <a name="see-also"></a>参照  
 [ユーザー定義型を作成する](../../relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types.md)  
  
  
