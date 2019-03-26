---
title: Oracle CDC インスタンスのデータ型 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: eec13d8d-c15a-4542-bfc4-da66b1a6bfe0
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2f373cf121a0368508e9b4b3380ef5c674a9fc9f
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2019
ms.locfileid: "58271674"
---
# <a name="oracle-cdc-instance-data-types"></a>Oracle CDC インスタンスのデータ型
  Oracle CDC インスタンスでは、ほとんどの Oracle データ型がサポートされます。 次のセクションでは、サポートされるデータ型とサポートされないデータ型について説明します。  
  
## <a name="supported-data-types"></a>サポートされるデータ型  
 次の表では、キャプチャできる Oracle データ型と、変更テーブルの SQL Server データ型に対する既定のマッピングについて説明します。 ソース Oracle テーブルにキャプチャ インスタンスを追加するときは、これらのマッピングをオーバーライドすることができます。  
  
|Oracle データベース データ型|SQL Server データ型|  
|-------------------------------|--------------------------|  
|BINARY_FLOAT|real|  
|BINARY_DOUBLE|FLOAT|  
|CHAR|NVARCHAR|  
|DATE|DATETIME|  
|FLOAT|FLOAT|  
|INT|NUMERIC (38)|  
|INTERVAL|DATETIME|  
|NCHAR|NVARCHAR|  
|NUMBER|FLOAT|  
|NAVARCHAR2|NVARCHAR|  
|RAW|VARBINARY|  
|real|FLOAT|  
|TIMESTAMP|DATETIME2|  
|TIMESTAMP WITH TIME ZONE|VARCHAR (37)|  
|TIMESTAMP WITH LOCAL TIME ZONE|VARCHAR (37)|  
|VARCHAR2|VARCHAR|  
|XMLTYPE|NVARCHAR (MAX)|  
  
## <a name="non-supported-data-types"></a>サポートされないデータ型  
 次の Oracle データ型の列を含むソース Oracle テーブルはキャプチャできません。 これらのデータ型を含むキャプチャ対象列は NULL として表示されます。ただし、これらの値の変更は、キャプチャ対象テーブルの変更マスクに示されます。  
  
-   LONG  
  
-   XMLTYPE  
  
-   BLOB  
  
-   CLOB  
  
 次の Oracle データ型の列を含むソース Oracle テーブルはキャプチャできません。  
  
-   BFILE  
  
-   ROWID  
  
-   REF  
  
-   UROWID  
  
-   入れ子になったテーブル  
  
 テーブルに次のデータ型が存在する場合、LogMinder はそのテーブルの列のデータを取得できません。  
  
-   ユーザー定義のデータ型  
  
-   VARRAY  
  
## <a name="see-also"></a>参照  
 [Attunity の Change Data Capture Designer for Oracle](../../integration-services/change-data-capture/change-data-capture-designer-for-oracle-by-attunity.md)   
 [Oracle CDC インスタンス](../../integration-services/change-data-capture/the-oracle-cdc-instance.md)  
  
  
