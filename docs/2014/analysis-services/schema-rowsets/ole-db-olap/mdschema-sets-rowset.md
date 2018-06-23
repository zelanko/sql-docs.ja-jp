---
title: MDSCHEMA_SETS 行セット |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MDSCHEMA_SETS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_SETS rowset
ms.assetid: abb00dc0-2b83-48d6-b2ba-6615c1488d06
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: edc33b87256fb680225eaaa087ff655be1b82851
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178567"
---
# <a name="mdschemasets-rowset"></a>MDSCHEMA_SETS 行セット
  データベースで現在定義されているセットについて記述します。セッション スコープのセットも含まれます。  
  
## <a name="rowset-columns"></a>行セットの列  
 `MDSCHEMA_SETS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||データベースの名前。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||サポートされていません。|  
|`CUBE_NAME`|`DBTYPE_WSTR`||キューブの名前。|  
|`SET_NAME`|`DBTYPE_WSTR`||`CREATE SET` ステートメントで指定されたセットの名前。|  
|`SCOPE`|`DBTYPE_I4`||セットのスコープ。<br /><br /> -   `MDSET_SCOPE_GLOBAL` (`1`)<br />-   `MDSET_SCOPE_SESSION` (`2`)|  
|`DESCRIPTION`|`DBTYPE_WSTR`||サポートされていません。|  
|`EXPRESSION`|`DBTYPE_WSTR`||セットの式。|  
|`DIMENSIONS`|`DBTYPE_WSTR`||セットに含まれている階層のコンマ区切りの一覧。|  
|`SET_CAPTION`|`DBTYPE_WSTR`||セットに関連付けられたラベルまたはキャプション。 このラベルまたはキャプションは、主に表示目的に使用されます。|  
|`SET_DISPLAY_FOLDER`|`DBTYPE_WSTR`||セットを表示するためにクライアント アプリケーションが使用する、表示フォルダーのパスを識別する文字列です。 フォルダー レベルの区切り記号は、クライアント アプリケーションによって定義されます。 ツールおよびクライアントによって提供される[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、円記号 (\\) は、レベルの区切り記号。 複数の表示フォルダーを指定するには、セミコロン (;) を使用して、フォルダーを区切ります。|  
|`SET_EVALUATION_CONTEXT`|`DBTYPE_I4`||セットのコンテキスト。 セットは、静的セットまたは動的セットです。<br /><br /> この列は、次のいずれかの値になります。<br /><br /> -MDSET_RESOLUTION_STATIC = 1<br />-MDSET_RESOLUTION_DYNAMIC = 2|  
  
 行セットは、`CATALOG_NAME`、`SCHEMA_NAME`、`CUBE_NAME` を基準に並べ替えることができます。  
  
## <a name="restriction-columns"></a>制限の列  
 `MDSCHEMA_SETS`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|任意。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|任意。|  
|`CUBE_NAME`|`DBTYPE_WSTR`|任意。|  
|`SET_NAME`|`DBTYPE_WSTR`|任意。|  
|`SCOPE`|`DBTYPE_I4`|任意。|  
|`HIERARCHY_UNIQUE_NAME`|`DBTYPE_WSTR`|任意。|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|任意。 **注:** 1 つだけの階層が含まれることができますあり、名前付きセットのみが返される階層では、制限と正確に一致します。|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP Schema 行セット](ole-db-for-olap-schema-rowsets.md)  
  
  