---
title: "DISCOVER_LOCATIONS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: 6d3a1171-8e4d-4022-ade0-b785cf795d70
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 15828ba16158f97479010617a68a5f3a11cf185e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="discoverlocations-rowset"></a>DISCOVER_LOCATIONS 行セット
  バックアップ ファイルの内容に関する情報を返します。 バックアップ ファイルの場所にアクセスする権限が必要です。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_LOCATIONS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|制限|Description|  
|-----------------|--------------------|-----------------|-----------------|  
|**LOCATION_BACKUP_FILE_PATHNAME**|**DBTYPE_WSTR**|必須。以下を参照してください。|バックアップ ファイルの場所です。|  
|**LOCATION_PARTITION_OBJECTPATH**|**DBTYPE_WSTR**||データ フォルダーを基準とするパーティションのパスです。|  
|**LOCATION_PARTITION_DATASOURCEID**|**DBTYPE_WSTR**||パーティションの処理に使用されるデータ ソース ID です。|  
|**LOCATION_PARTITION_DATASOURCENAME**|**DBTYPE_WSTR**||処理に使用されるデータ ソースの名前です。|  
|**LOCATION_PARTITION_NAME**|**DBTYPE_WSTR**||パーティションの名前です。|  
|**LOCATION_PARTITION_SIZE**|**DBTYPE_WSTR**||パーティションのおおよそのサイズです。|  
|**LOCATION_CONNECTION_STRING**|**DBTYPE_WSTR**||処理で使用されるデータ ソースの接続文字列です。|  
|**LOCATION_PARTITION_FOLDER**|**DBTYPE_WSTR**||バックアップ ファイルが生成されたときの、このパーティションの元の場所です。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 **DISCOVER_LOCATIONS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**LOCATION_BACKUP_FILE_PATHNAME**|**DBTYPE_WSTR**|必須|  
|**LOCATION_PASSWORD PF_DBTYPE**|**DBTYPE_WSTR**|バックアップ中に指定された場合は必須。 この制限は、返される行を制限するためには使用されません。 場所にアクセスするためのパスワードを提供するために使用されます。|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd92-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|[場所]|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis スキーマ行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

