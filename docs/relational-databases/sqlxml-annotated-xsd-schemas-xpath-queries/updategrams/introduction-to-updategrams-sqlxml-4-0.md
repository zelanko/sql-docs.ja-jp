---
title: "アップデート グラム (SQLXML 4.0) の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- explicit schema mapping [SQLXML]
- updategrams [SQLXML], mapping schema specifying
- namespaces [SQLXML]
- updategrams [SQLXML], about updategrams
- attribute-centric mapping
- invalid characters [SQLXML]
- element-centric mapping [SQLXML]
- mapping schema [SQLXML], updategrams
- namespaces [SQLXML], updategrams
- executing updategrams [SQLXML]
- implicit schema mapping
ms.assetid: cfe24e82-a645-4f93-ab16-39c21f90cce6
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2dc3ce73bfe3da97e6567c1819eea34a8bc1dfaa
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="introduction-to-updategrams-sqlxml-40"></a>アップデートグラムの概要 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
変更することができます (挿入、更新、または削除) のデータベースに[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]アップデート グラムまたは OPENXML を使用してドキュメントの既存の XML から[!INCLUDE[tsql](../../../includes/tsql-md.md)]関数。  
  
 OPENXML 関数は、既存の XML ドキュメントを断片化し、INSERT、UPDATE または DELETE ステートメントに渡すことができる行セットを提供することで、データベースを変更する関数です。 OPENXML を使用すると、データベース テーブルに対して操作を直接実行できます。 したがって、ソースにテーブルなどの行セット プロバイダーがある場合は常に、OPENXML を使用するのが最適です。  
  
 アップデートグラムを使用すると、OPENXML と同様にデータベースに対してデータを挿入、更新、または削除できます。ただし、アップデートグラムは注釈付き XSD (または XDR) スキーマにより提供される XML ビューに対して動作します。たとえば、更新はマッピング スキーマにより提供される XML ビューに適用されます。 マッピング スキーマには、XML 要素と属性を対応するデータベース テーブルと列にマップするための、必要な情報が含まれています。 アップデートグラムでは、このマッピング情報を使用してデータベース テーブルと列が更新されます。  
  
> [!NOTE]  
>  このドキュメントは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でサポートされるテンプレートとマッピング スキーマについて理解していることを前提としています。 詳細については、次を参照してください[注釈付き XSD スキーマの選択 &#40; の概要。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md). XDR を使用する従来のアプリケーションでは、次を参照してください。[注釈付き XDR スキーマ &#40; SQLXML 4.0 &#41; で推奨されなくなった](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)です。  
  
## <a name="required-namespaces-in-the-updategram"></a>アップデートグラムで必要な名前空間  
 アップデート グラムのキーワードなど**\<同期 >**、 **\<する前に >**、および**\<後 >**、内に存在**urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql} のアップデート グラム**名前空間。 名前空間プレフィックスは、任意のものを使用できます。 このドキュメントで、 **updg**プレフィックスを示します、**アップデート グラム**名前空間。  
  
## <a name="reviewing-syntax"></a>構文の確認  
 アップデート グラムはテンプレートが**\<同期 >**、 **\<する前に >**、および**\<後 >**ブロックの構文を形成する、アップデート グラムです。 次のコードは、最も単純な構文です。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema= "AnnotatedSchemaFile.xml"] >  
    <updg:before>  
        ...  
    </updg:before>  
    <updg:after>  
        ...  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 次に、これらの各ブロックの役割について説明します。  
  
 **\<before>**  
 レコード インスタンスの既存の状態 ("before 状態") を指定します。  
  
 **\<after>**  
 データの変更後の新しい状態を指定します。  
  
 **\<sync>**  
 含まれています、 **\<する前に >**と**\<後 >**ブロックします。 A **\<同期 >**ブロックは 1 つ以上のセットを含めることができます**\<する前に >**と**\<後 >**ブロックします。 1 つ以上のセットがある場合**\<する前に >**と**\<後 >**ブロック、これらのブロック (でも場合は、空) 指定する必要のペアとして。 さらに、アップデート グラムでは 1 つ以上**\<同期 >**ブロックします。 各**\<同期 >**ブロックは、トランザクションの 1 つの単位 (つまり、すべてのオブジェクト、 **\<同期 >**ブロックが実行されるか、何も行わ)。 複数指定する場合**\<同期 >**アップデート グラムでは、1 つの障害でブロック**\<同期 >**ブロックには影響しません、他の**\<同期>**ブロックします。  
  
 かどうか、アップデート グラムを削除、挿入、または更新レコード インスタンスの内容に応じた、 **\<する前に >**と**\<後 >**ブロック。  
  
-   レコード インスタンスがでのみが表示された場合、 **\<する前に >**ブロックに対応するインスタンスを**\<後 >**ブロック、アップデート グラムでは、削除操作を実行します。  
  
-   レコード インスタンスがでのみが表示された場合、 **\<後 >**ブロックに対応するインスタンスを**\<する前に >**ブロック、挿入操作であります。  
  
-   レコード インスタンスが表示される場合、 **\<する前に >**をブロックして、対応するインスタンスが、 **\<後 >**ブロックは、更新操作。 この場合、アップデート グラムがで指定されている値にレコード インスタンスが更新、 **\<後 >**ブロックします。  
  
## <a name="specifying-a-mapping-schema-in-the-updategram"></a>アップデート グラムでマッピング スキーマの指定  
 アップデートグラムでは、暗黙的または明示的に、マッピング スキーマによって XML データを操作できます。つまり、マッピング スキーマを指定しても指定しなくてもアップデートグラムは動作します。マッピング スキーマは XSD と XDR の両方がサポートされています。 マッピング スキーマを指定しない場合、アップデート グラムが暗黙的なマッピング (既定のマッピング) を前提としていますここで、内の各要素、 **\<する前に >**ブロックまたは**\<後 >**ブロックは、テーブルと各要素の子要素にマップまたは属性は、データベース内の列にマップします。 マッピング スキーマを明示的に指定する場合、アップデートグラムの要素と属性は、マッピング スキーマ内の要素と属性に一致する必要があります。  
  
### <a name="implicit-default-mapping"></a>暗黙的なマッピング (既定)  
 単純な更新を実行するアップデートグラムではほとんどの場合、マッピング スキーマは必要ありません。 この場合、アップデートグラムは既定のマッピング スキーマに従います。  
  
 次のアップデート グラムは、暗黙的なマッピングを示しています。 この例では、アップデートグラムによって新しい顧客が Sales.Customer テーブルに挿入されます。 このアップデート グラムでは、暗黙的なマッピングを使用するため、 \<Sales.Customer > 要素は Sales.Customer テーブルにマップされ、CustomerID および SalesPersonID 属性は Sales.Customer テーブルの対応する列にマップします。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
</updg:before>  
<updg:after>  
    <Sales.Customer CustomerID="1" SalesPersonID="277" />  
    </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="explicit-mapping"></a>明示的なマッピング  
 XSD または XDR のいずれかのマッピング スキーマを指定した場合、アップデートグラムではそのスキーマによって、更新するデータベース テーブルと列が決定されます。  
  
 使用して、マッピング スキーマを明示的に指定する必要があります、アップデート グラムでは、複雑な更新プログラム (たとえば、マッピング スキーマで指定されている親子リレーションシップに基づいて複数のテーブルに挿入するレコード) を実行する場合、 **マッピング スキーマ**属性に対して、アップデート グラムを実行します。  
  
 アップデートグラムはテンプレートであり、アップデートグラム内でマッピング スキーマに指定するパスは、テンプレート ファイルの場所 (アップデートグラムが保存されている場所) に対する相対パスです。 詳細については、次を参照してください[アップデート グラム &#40; での注釈付きマッピング スキーマの指定。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
## <a name="element-centric-and-attribute-centric-mapping-in-updategrams"></a>アップデートグラムでの要素中心および属性中心のマッピング  
 アップデートグラムでマッピング スキーマが指定されていないときに使用される既定のマッピングでは、アップデートグラムの要素がテーブルにマップされ、要素中心マッピングの場合は子要素、属性中心マッピングの場合は属性が、それぞれ列にマップされます。  
  
### <a name="element-centric-mapping"></a>要素中心のマッピング  
 要素中心のアップデートグラムでは、要素に、要素のプロパティを表す子要素を含めます。 たとえば、次のアップデートグラムを参照してください。 **\<Person.Contact >**要素が含まれています、  **\<FirstName >**と **\<LastName >**子要素です。 これらの子要素のプロパティは、  **\<Person.Contact >**要素。  
  
 このアップデート グラムでは、マッピング スキーマを指定しないので、アップデート グラムでは暗黙的なマッピングを使用している、  **\<Person.Contact >**要素は Person.Contact テーブルにマップされ、その子要素が firstname マップとLastName 列です。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:after>  
    <Person.Contact>  
       <FirstName>Catherine</FirstName>  
       <LastName>Abel</LastName>  
    </Person.Contact>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="attribute-centric-mapping"></a>属性中心のマッピング  
 属性中心のマッピングでは、要素に属性を指定します。 たとえば、次のアップデートグラムでは属性中心のマッピングが使用されています。 この例では、  **\<Person.Contact >**要素から成る、 **FirstName**と**LastName**属性。 これらの属性のプロパティ、  **\<Person.Contact >**要素。 前の例では、このアップデート グラムでスキーマを指定しないマッピング、暗黙の型をマップするマッピングに依存しているため、  **\<Person.Contact >**要素は Person.Contact テーブルと、要素の属性をテーブル内の各列。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
    <Person.Contact FirstName="Catherine" LastName="Abel" />  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
### <a name="using-both-element-centric-and-attribute-centric-mapping"></a>要素中心と属性中心の両方のマッピングの使用  
 次のアップデートグラムに示すように、要素中心と属性中心のマッピングは併用できます。 注意して、  **\<Person.Contact >**要素には、属性と子要素の両方が含まれています。 また、このアップデートグラムは暗黙的なマッピングに従います。 したがって、 **FirstName**属性および **\<LastName >**子要素は Person.Contact テーブル内の対応する列にマップします。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
    <Person.Contact FirstName="Catherine" >  
       <LastName>Abel</LastName>  
    </Person.Contact>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
## <a name="working-with-characters-valid-in-sql-server-but-not-valid-in-xml"></a>SQL Server で有効であり、XML で有効でない文字の取り扱い  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、テーブル名に空白を含めることができます。 ただし、このようなテーブル名は XML では有効でありません。  
  
 無効な文字をエンコードする[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]識別子が有効な XML 識別子をだが、使用して '__xHHHH\_\_' HHHH は、ほとんどの文字の 4 桁の 16 進数 ucs-2 コード エンコーディングの値として上位ビットから順です。 このエンコード方式を使用して、空白文字を取得置き換え x0020 (4 桁 16 進数のコード、空白文字) です。したがって、内のテーブル名 [Order Details] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] _x005B_Order_x0020_Details_x005D になります\_XML 内です。  
  
 同様になどの 3 つの部分の要素の名前を指定する必要があります\<[データベース]. [所有者] です。[テーブル] >。 角かっこ ([と]) は、XML では無効なとしてを指定する必要がありますので\<_x005B_database_x005D\_._x005B_owner_x005D\_._x005B_table_x005D\_> ここで、_x005B\_は、左角かっこ ([) と _x005D のエンコード\_右角かっこ (]) のエンコーディングします。  
  
## <a name="executing-updategrams"></a>アップデートグラムの実行  
 アップデートグラムはテンプレートであり、テンプレートのすべての処理メカニズムが適用されます。 SQLXML 4.0 では、アップデートグラムを次のいずれかの方法で実行できます。  
  
-   ADO コマンドに含めて送信する。  
  
-   OLE DB コマンドとして送信する。  
  
## <a name="see-also"></a>参照  
 [アップデート グラムのセキュリティに関する考慮事項 &#40;です。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
