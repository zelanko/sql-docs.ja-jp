---
title: DISCOVER_LOCKS 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7f0b52b875793df4074e9feb4e0cc1737224a901
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34031763"
---
# <a name="discoverlocks-rowset"></a>DISCOVER_LOCKS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  サーバー上で現在保持されているロックに関する情報を提供します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_LOCKS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**LOCK_CREATION_TIME**|**DBTYPE_DBTIMESTAMP**||ロックが要求されたときの UTC サーバー時刻。|  
|**LOCK_GRANT_TIME**|**DBTYPE_DBTIMESTAMP**||リソースのロックが許可されたときの UTC サーバー時刻。|  
|**LOCK_ID**|**DBTYPE_GUID 型**||GUID としてのロックの一意識別子。|  
|**LOCK_OBJECT_ID**|**DBTYPE_WSTR**||ロックされているオブジェクトの一意識別子。|  
|**LOCK_STATUS**|**DBTYPE_I4**||ロックの状態。<br /><br /> 0 は "オブジェクトをロックするのを待機している" 状態を意味します。<br /><br /> 1 は "ロックが許可された" 状態を意味します。|  
|**LOCK_TRANSACTION_ID**|**DBTYPE_GUID 型**||GUID としてのトランザクションの一意識別子。|  
|**LOCK_TYPE**|**DBTYPE_I4**||ロックの種類を表すビット マスク。詳細については、このトピックの「解説」を参照してください。|  
|**SPID**|**DBTYPE_I4**||セッション ID。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 **DISCOVER_LOCKS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|SPID|DBTYPE_I4|省略可。|  
|LOCK_TRANSACTION_ID|DBTYPE_GUID|省略可。|  
|LOCK_OBJECT_ID|DBTYPE_WSTR|省略可。|  
|LOCK_STATUS|DBTYPE_I4|省略可。|  
|LOCK_TYPE|DBTYPE_I4|省略可。|  
|LOCK_MIN_TOTAL_MS|DBTYPE_I8|省略可。|  
  
## <a name="remarks"></a>解説  
  
## <a name="lock-types"></a>ロックの種類  
  
|ロック名|値|Description|  
|---------------|-----------|-----------------|  
|LOCK_NONE|0x0000000|ロックなし。|  
|LOCK_SESSION_LOCK|0x0000001|非アクティブなセッション。他のロックには影響しません。|  
|LOCK_READ|0x0000002|処理中の読み取りロック。|  
|LOCK_WRITE|0x0000004|処理中の書き込みロック。|  
|LOCK_COMMIT_READ|0x0000008|コミット ロック (共有)。|  
|LOCK_COMMIT_WRITE|0x0000010|コミット ロック (排他)。|  
|LOCK_COMMIT_ABORTABLE|0x0000020|コミット進行中に中止。|  
|LOCK_COMMIT_INPROGRESS|0x0000040|コミット進行中。|  
|LOCK_INVALID|0x0000080|無効なロック。|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis スキーマ行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  
