---
title: XML アップデート グラム (SQLXML 4.0) を使用してデータを削除する |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- <after> block
- updategrams [SQLXML], deleting data
- <before> block
- mapping-schema attribute
- record deletions [SQLXML]
ms.assetid: 4fb116d7-7652-474a-a567-cb475a20765c
caps.latest.revision: 23
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 32134713be17a0770eb58d69529cc34691c181a5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085619"
---
# <a name="deleting-data-using-xml-updategrams-sqlxml-40"></a>XML アップデートグラムを使用した、データの削除 (SQLXML 4.0)
  レコード インスタンスが表示されたら、アップデート グラムは削除操作を示す、 **\<する前に >** に対応するレコードのないブロック、 **\<後 >** ブロックします。 この場合、アップデート グラムでレコードを削除、 **\<する前に >** データベースからブロックされます。  
  
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
  
 省略することができます、 **\<後 >** アップデート グラムでは削除操作のみを実行する場合にタグ付けします。 省略可能な指定しない場合`mapping-schema`、属性、  **\<ElementName >** アップデート グラムで、データベース テーブルにマップし、子要素または属性にマップ テーブル内の列で指定します。  
  
 アップデート グラムではエラーが返され、全体を取り消す場合は、アップデート グラムで指定される要素は、テーブル内の 1 つ以上の行と一致するか、任意の行と一致しません、 **\<同期 >** ブロックします。 アップデートグラム内の要素で削除できるのは、一度に 1 つのレコードだけです。  
  
## <a name="examples"></a>使用例  
 この例では、アップデートグラムでマッピング スキーマを指定せず、既定のマッピングを使用します。 マッピング スキーマを使用するアップデート グラムの例については、次を参照してください。[アップデート グラムの注釈付きマッピング スキーマの指定&#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)です。  
  
 次の例を使用して実際のサンプルを作成するで指定された要件を満たす必要がある[SQLXML の例を実行するための要件](../../sqlxml/requirements-for-running-sqlxml-examples.md)です。  
  
### <a name="a-deleting-a-record-by-using-an-updategram"></a>A. アップデートグラムを使用してレコードを削除する  
 次のアップデートグラムでは、HumanResources.Shift テーブルから 2 つのレコードを削除します。  
  
 この例のアップデートグラムでは、マッピング スキーマを指定しません。 したがって、アップデートグラムでは既定のマッピングが使用されます。このマッピングでは、要素名はテーブル名にマップされ、属性または副要素は列にマップされます。  
  
 最初のアップデート グラムは属性中心とで 2 つのシフト (日中から夕方と夕方から夜) を識別、 **\<する前に >** ブロックします。 対応するレコードがないため、 **\<後 >** ブロック、これは、削除操作です。  
  
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
  
1.  完全な例 ("複数のレコードを使用した挿入アップデート グラム") で B[を挿入するデータを使用して XML アップデート グラム&#40;SQLXML 4.0&#41;](inserting-data-using-xml-updategrams-sqlxml-4-0.md)です。  
  
2.  上のアップデート グラムをメモ帳にコピーしで ("複数のレコードを使用した挿入アップデート グラム") を完了するために使用された同じフォルダーに Updategram-removeshifts.xml として保存[を挿入するデータを使用して XML アップデート グラム&#40;SQLXML 4.0&#41;](inserting-data-using-xml-updategrams-sqlxml-4-0.md).  
  
3.  SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。  
  
     詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に使用する ADO](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)です。  
  
## <a name="see-also"></a>参照  
 [アップデート グラムのセキュリティに関する考慮事項&#40;SQLXML 4.0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  