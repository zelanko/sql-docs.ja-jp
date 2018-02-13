---
title: "注釈付きスキーマのセキュリティに関する注意点 (SQLXML 4.0) |Microsoft ドキュメント"
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
- mapping schema [SQLXML], security
- annotated XDR schemas, security
- XDR schemas [SQLXML], security
- annotations [SQLXML]
- annotated XSD schemas, security
- SQLXML, annotated XSD schemas
- SQLXML, annotated XDR schemas
- security [SQLXML], annotated schemas
- XSD schemas [SQLXML], security
ms.assetid: 7d7e44dc-b6d3-4e0f-95c7-8f99930c94f2
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 14f7bffc4d448a40ce3de215f9228315d8667d0d
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="annotated-schema-security-considerations-sqlxml-40"></a>注釈付きスキーマのセキュリティに関する注意点 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
次に、注釈付きスキーマを使用する場合のセキュリティに関するガイドラインを示します。  
  
-   マッピング スキーマでは既定のマッピングを使用しないようにしてください。 既定のマッピングでは、要素名がテーブル名にマップされ、属性名が列名にマップされるため、結果の XML ドキュメントではデータベース情報 (テーブル名と列名) が公開されることになります。 データベースのテーブルと列の情報には XML ドキュメントを表示できるユーザーであればだれでもアクセスできるので、これにより、セキュリティが脅かされる可能性があります。 この危険を避けるため、スキーマで任意の要素名と属性名を指定し、注釈を使用してそれらを明示的にテーブルと列にマップするようにしてください。 詳細については、XSD スキーマを作成するときに既定のマッピングを使用して、次を参照してください。[既定のマッピングの XSD 要素と属性をテーブルと列 &#40;です。SQLXML 4.0 &#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md).  
  
-   注釈を使用して指定する明示的なマッピングでは、データベース情報 (テーブル名、列名など) が公開されます。 このため、これらのスキーマはだれもがアクセスできる場所に置かないことをお勧めします。  
  
-   再帰ではマッピング スキーマに対して指定されているなどの特定のクエリ (を使用して指定**深さの最大**注釈を大きい値に設定) の実行に長い時間かかる場合があります。 秒単位で、コマンド タイムアウト プロパティを設定して、必要に応じてタイムアウトの制限を指定することができます。 例:  
  
    ```  
    cn.Open "Provider=SQLOLEDB;Server=localhost;Database=tempdb;Integrated Security=SSPI;Command Properties='Command Time Out=50';"  
    ```  
  
## <a name="see-also"></a>参照  
 [SQLXML 4.0 の注釈付き XSD スキーマ](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xsd-schemas-in-sqlxml-4-0.md)  
  
  
