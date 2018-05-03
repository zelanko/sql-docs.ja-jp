---
title: スキーマ セクション |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Schema section [ADO]
ms.assetid: 4ac6e524-2c92-48e8-b871-0a4b5c8fda18
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7614a2c23d21d88652c32fef480367df4db65be8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="schema-section"></a>スキーマ セクション
スキーマのセクションが必要です。 前の例に示すように、ADO は更新可能な限り、データ値のセマンティクスを保持するために各列に関する詳細なメタデータを書き込みます。 ただし、XML に読み込むには、ADO のみが必要ですが所属する行セットおよび列の名前。 最小限のスキーマの例を次に示します。  
  
```  
<xml xmlns:s="uuid:BDC6E3F0-6DA3-11d1-A2A3-00AA00C14882"  
    xmlns:rs="urn:schemas-microsoft-com:rowset"  
    xmlns:z="#RowsetSchema">  
  <s:Schema id="RowsetSchema">  
    <s:ElementType name="row" content="eltOnly">  
      <s:AttributeType name="ShipperID"/>  
      <s:AttributeType name="CompanyName"/>  
      <s:AttributeType name="Phone"/>  
      <s:Extends type="rs:rowbase"/>  
    </s:ElementType>  
  </s:Schema>  
  <rs:data>  
...  
  </rs:data>  
</xml>  
```  
  
 前の例では、スキーマで型情報が含まれていないために、ADO は可変長文字列としてデータを扱います。  
  
## <a name="creating-aliases-for-column-names"></a>列名のエイリアスの作成  
 Rs: name 属性では、フレンドリ名は、行セットによって公開されている列の情報になっている可能性があり、データ セクションに、短い名前を使用することがありますように列名のエイリアスを作成することができます。 たとえば、s1、s2 に CompanyName を運送をマップし、次のように s3 に電話を前のスキーマを変更できませんでした。  
  
```  
<s:Schema id="RowsetSchema">   
<s:ElementType name="row" content="eltOnly" rs:updatable="true">   
<s:AttributeType name="s1" rs:name="ShipperID" rs:number="1" ...>   
...  
</s:AttributeType>   
<s:AttributeType name="s2" rs:name="CompanyName" rs:number="2" ...>   
...  
</s:AttributeType>   
<s:AttributeType name="s3" rs:name="Phone" rs:number="3" ...>   
...  
</s:AttributeType>   
...  
</s:ElementType>   
</s:Schema>  
```  
  
 次に、data セクションで、行は、名前属性を使用して (rs: 名ではなく) その列を参照してください。  
  
```  
"<row s1="1" s2="Speedy Express" s3="(503) 555-9831"/>  
```  
  
 列名のエイリアスを作成するには、必ず、列名が有効な属性または XML タグ名がありません。 たとえば、"LastName"は別名を持つ必要がありますに埋め込まれたスペース名が無効な属性であるためです。 次の行は正しく処理されません、XML パーサーによってため、埋め込みスペースがない別の名前に別名を作成する必要があります。  
  
```  
<row last name="Jones"/>  
```  
  
 Name 属性を使用するどのような値は、XML ドキュメントのスキーマとデータの両方のセクションで、列が参照されている各場所で常に使用する必要があります。 次の例は、s1 の一貫した使用法を示しています。  
  
```  
<s:Schema id="RowsetSchema">  
  <s:ElementType name="row" content="eltOnly">  
    <s:attribute type="s1"/>  
    <s:attribute type="CompanyName"/>  
    <s:attribute type="s3"/>  
    <s:extends type="rs:rowbase"/>  
  </s:ElementType>  
  <s:AttributeType name="s1" rs:name="ShipperID" rs:number="1"   
    rs:maydefer="true" rs:writeunknown="true">  
    <s:datatype dt:type="i4" dt:maxLength="4" rs:precision="10"   
      rs:fixedlength="true" rs:maybenull="true"/>  
  </s:AttributeType>  
</s:Schema>  
<rs:data>  
  <z:row s1="1" CompanyName="Speedy Express" s3="(503) 555-9831"/>  
</rs:data>  
```  
  
 同様があるためエイリアスに対して定義されていない`CompanyName`前の例では、`CompanyName`ドキュメント全体で一貫して使用する必要があります。  
  
## <a name="data-types"></a>データ型  
 データ型は、dt:type 属性を持つ列に適用できます。 使用できる XML 型の明確なガイドは、データ型を参照してください、 [W3C の XML データの指定](http://www.w3.org/TR/1998/NOTE-XML-data/)です。 2 つの方法でデータの種類を指定することができます。 列の定義自体で直接 dt:type 属性を指定するか、列定義の入れ子になった要素として s:datatype コンストラクトを使用します。 例を次に示します。  
  
```  
<s:AttributeType name="Phone" >  
  <s:datatype dt:type="string"/>  
</s:AttributeType>  
```  
  
 等価します。  
  
```  
<s:AttributeType name="Phone" dt:type="string"/>  
```  
  
 既定では行の定義全体から dt:type 属性を省略した場合、列の型は可変長の文字列になります。  
  
 単純型名 (たとえば、dt:maxLength) よりも多くの型情報があれば、そのことが見やすくなります s:datatype 子要素を使用します。 これは、単なる慣習、ただし、および要件ではありません。  
  
 次の例では、さらに、スキーマに型情報を含める方法を示します。  
  
```  
<!-- 1. String with no max length -->  
<s:AttributeType name="title_id"/>  
<!—or -->  
<s:AttributeType name="title_id" dt:type="string"/>  
  
<!—- 2. Fixed length string with max length of 6 -->  
<s:AttributeType name="title_id">  
    <s:datatype dt:type="string" dt:maxLength="6" rs:fixedlength="true" />  
</s:AttributeType>  
  
<!—- 3. Variable length string with max length of 6 -->  
<s:AttributeType name="title_id">  
    <s:datatype dt:type="string" dt:maxLength="6" />  
</s:AttributeType>  
  
<!—- 4. Integer -->  
<s:AttributeType name="title_id" dt:type="int"/>  
```  
  
 2 番目の例では、rs: fixedlength 属性の微妙な使用があります。 Rs: fixedlength 属性を持つ列は、true の場合は、データがスキーマで定義された長さの必要なに設定します。 この場合、title_id の有効な値は「123456」、「123」は、 ただし、「123」はできません。 有効な長さが 3、6 ではなくです。 Fixedlength プロパティの説明を完了より OLE DB プログラマ ガイドを参照してください。  
  
## <a name="handling-nulls"></a>Null 値を処理  
 Null 値は、rs: maybenull 属性によって処理されます。 この属性に設定されている場合は true、列の内容は、null 値を含めることができます。 さらに、行のデータの列が見つからない場合、行セットから返されたデータを読み取るユーザーは、null 状態 irowset::getdata() から受け取ります。 Shippers テーブルから次の列の定義を検討してください。  
  
```  
<s:AttributeType name="ShipperID">  
  <s:datatype dt:type="int" dt:maxLength="4"/>  
</s:AttributeType>  
<s:AttributeType name="CompanyName">  
  <s:datatype dt:type="string" dt:maxLength="40" rs:maybenull="true"/>  
</s:AttributeType>  
```  
  
 定義により`CompanyName`、null にすることが、 `ShipperID` null 値を含めることはできません。 データ セクションには、次の行が含まれている、永続化プロバイダーは設定のデータの状態、 `CompanyName` OLE DB 状態定数 DBSTATUS_S_ISNULL 列。  
  
```  
<z:row ShipperID="1"/>  
```  
  
 場合は、行全体が空でした、次のように、永続化プロバイダーは、OLE DB のリターン ステータスに DBSTATUS_E_UNAVAILABLE`ShipperID`と CompanyName を DBSTATUS_S_ISNULL です。  
  
```  
<z:row/>   
```  
  
 長さ 0 の文字列がいない null の場合と同じに注意してください。  
  
```  
<z:row ShipperID="1" CompanyName=""/>  
```  
  
 前の行では、永続化プロバイダーは、OLE DB の状態が DBSTATUS_S_OK 両方の列を返します。 `CompanyName`ここでは単に""(長さ 0 の文字列)。  
  
 詳細については、OLE DB 構造は OLE DB の XML ドキュメントのスキーマ内で使用できるの定義を参照してください"urn: スキーマ-microsoft-com:rowset"と OLE DB プログラマ ガイドです。  
  
## <a name="see-also"></a>参照  
 [レコードを XML 形式で保持する](../../../ado/guide/data/persisting-records-in-xml-format.md)
