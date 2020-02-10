---
title: XML アップデートグラムを使用したデータの削除 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- <after> block
- updategrams [SQLXML], deleting data
- <before> block
- mapping-schema attribute
- record deletions [SQLXML]
ms.assetid: 4fb116d7-7652-474a-a567-cb475a20765c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 444ef7d8c95b0cbd41ba3fbb55a6fbeb30870462
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66014868"
---
# <a name="deleting-data-using-xml-updategrams-sqlxml-40"></a>XML アップデートグラムを使用した、データの削除 (SQLXML 4.0)
  アップデートグラムは、レコードインスタンスが** \<after>** ブロックに対応するレコードがない>ブロックの** \<前**にある場合に、削除操作を示します。 この場合、アップデートグラムでは、 ** \<データベースから before>** ブロックのレコードが削除されます。  
  
 削除操作のアップデートグラムの形式は次のとおりです。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema="SampleSchema.xml"]  >  
   <updg:before>  
       <ElementName />  
      [<ElementName .../>... ]  
   </updg:before>  
    [<updg:after>  
    </updg:after>]  
  </updg:sync>  
</ROOT>  
```  
  
 アップデートグラムが削除操作のみを実行している場合は、 ** \<after>** タグを省略できます。 省略可能`mapping-schema`な属性を指定しない場合、アップデートグラムで指定した** \<ElementName>** はデータベーステーブルにマップされ、子要素または属性はテーブル内の列にマップされます。  
  
 アップデートグラムで指定された要素が、テーブル内の複数の行に一致するか、いずれの行とも一致しない場合、アップデートグラムはエラーを返し、 ** \<同期>** ブロック全体をキャンセルします。 アップデートグラム内の要素で削除できるのは、一度に 1 つのレコードだけです。  
  
## <a name="examples"></a>例  
 この例では、アップデートグラムでマッピング スキーマを指定せず、既定のマッピングを使用します。 マッピングスキーマを使用するアップデートグラムの例については、「[アップデートグラムでの注釈付きマッピングスキーマの指定 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)」を参照してください。  
  
 次の例を使用して実際のサンプルを作成するには、 [SQLXML の例を実行するための要件](../../sqlxml/requirements-for-running-sqlxml-examples.md)を満たす必要があります。  
  
### <a name="a-deleting-a-record-by-using-an-updategram"></a>A. アップデートグラムを使用してレコードを削除する  
 次のアップデートグラムでは、HumanResources.Shift テーブルから 2 つのレコードを削除します。  
  
 この例のアップデートグラムでは、マッピング スキーマを指定しません。 したがって、アップデートグラムでは既定のマッピングが使用されます。このマッピングでは、要素名はテーブル名にマップされ、属性または副要素は列にマップされます。  
  
 この最初のアップデートグラムは属性中心であり、 ** \<before>** ブロックの2つのシフト (日、夜、夜) を識別します。 >ブロックの** \<後**に対応するレコードがないため、これは削除操作です。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
  <updg:before>  
       <HumanResources.Shift ShiftID="4"  
                        Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift ShiftID="5"  
                        Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
  </updg:before>  
  <updg:after>  
  </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>アップデートグラムをテストするには  
  
1.  「 [XML アップデートグラムを使用してデータを挿入する](inserting-data-using-xml-updategrams-sqlxml-4-0.md)」の例 B (「アップデートグラムを使用して複数のレコードを挿入する」) を実行します。 &#40;SQLXML 4.0&#41;。  
  
2.  上記のアップデートグラムをメモ帳にコピーし、Updategram-RemoveShifts として保存したのと同じフォルダー (「アップデートグラムを使用して複数のレコードを挿入する」) で、「 [Xml アップデート&#41;4.0 &#40;グラム](inserting-data-using-xml-updategrams-sqlxml-4-0.md)を使用してデータを挿入する」に記載されているものと同じフォルダーにとして保存します。  
  
3.  SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。  
  
     詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQLXML 4.0&#41;&#40;アップデートグラムのセキュリティに関する考慮事項](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
