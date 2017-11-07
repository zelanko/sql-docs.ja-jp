---
title: "MDSCHEMA_SETS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MDSCHEMA_SETS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_SETS rowset
ms.assetid: abb00dc0-2b83-48d6-b2ba-6615c1488d06
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4820c18992da2aab0ac8e0550a5cadd75ca193bc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="mdschemasets-rowset"></a>MDSCHEMA_SETS 行セット
  データベースで現在定義されているセットについて記述します。セッション スコープのセットも含まれます。  
  
## <a name="rowset-columns"></a>行セットの列  
 **MDSCHEMA_SETS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|Description|  
|-----------------|--------------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|データベースの名前。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|サポートされていません。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|キューブの名前。|  
|**SET_NAME**|**DBTYPE_WSTR**|指定されたセットの名前、 **CREATE SET**ステートメントです。|  
|**スコープ**|**DBTYPE_I4**|セットのスコープ。<br /><br /> **MDSET_SCOPE_GLOBAL** (**1**)<br /><br /> **MDSET_SCOPE_SESSION** (**2**)|  
|**DESCRIPTION**|**DBTYPE_WSTR**|サポートされていません。|  
|**式**|**DBTYPE_WSTR**|セットの式。|  
|**ディメンション**|**DBTYPE_WSTR**|セットに含まれている階層のコンマ区切りの一覧。|  
|**SET_CAPTION**|**DBTYPE_WSTR**|セットに関連付けられたラベルまたはキャプション。 このラベルまたはキャプションは、主に表示目的に使用されます。|  
|**SET_DISPLAY_FOLDER**|**DBTYPE_WSTR**|セットを表示するためにクライアント アプリケーションが使用する、表示フォルダーのパスを識別する文字列です。 フォルダー レベルの区切り記号は、クライアント アプリケーションによって定義されます。 ツールおよびクライアントによって提供される[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、円記号 (\\) は、レベルの区切り記号。 複数の表示フォルダーを指定するには、セミコロン (;) を使用して、フォルダーを区切ります。|  
|**SET_EVALUATION_CONTEXT**|**DBTYPE_I4**|セットのコンテキスト。 セットは、静的セットまたは動的セットです。 この列は、次のいずれかの値になります。<br /><br /> MDSET_RESOLUTION_STATIC=1<br /><br /> MDSET_RESOLUTION_DYNAMIC=2|  
  
 行セットが並べ替えられて**CATALOG_NAME**、 **SCHEMA_NAME**、 **CUBE_NAME**です。  
  
## <a name="restriction-columns"></a>制限の列  
 **MDSCHEMA_SETS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|省略可。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|省略可。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**SET_NAME**|**DBTYPE_WSTR**|省略可。|  
|**スコープ**|**DBTYPE_I4**|省略可。|  
|**HIERARCHY_UNIQUE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|省略可。<br /><br /> 注: 1 つだけの階層が含まれることができますあり、名前付きセットのみが返される階層では、制限と正確に一致します。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP スキーマ行セット](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  

