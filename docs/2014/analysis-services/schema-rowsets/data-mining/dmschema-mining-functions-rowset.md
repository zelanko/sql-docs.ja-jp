---
title: DMSCHEMA_MINING_FUNCTIONS 行セット |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DMSCHEMA_MINING_FUNCTIONS
topic_type:
- apiref
helpviewer_keywords:
- DMSCHEMA_MINING_FUNCTIONS rowset
ms.assetid: 9ace7493-a7b1-45ca-93de-3cb2f3597017
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3b726c81df5a6085ee52b177d95b4917d7cb8be1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169649"
---
# <a name="dmschemaminingfunctions-rowset"></a>DMSCHEMA_MINING_FUNCTIONS 行セット
  実行しているサーバーで使用可能なデータ マイニング アルゴリズムでサポートされているデータ マイニング関数について説明します[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `DMSCHEMA_MINING_FUNCTIONS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`||アルゴリズムの名前。|  
|`FUNCTION_NAME`|`DBTYPE_WSTR`||関数の名前です。|  
|`FUNCTION_SIGNATURE`|`DBTYPE_WSTR`||関数の署名。|  
|`RETURNS_TABLE`|`DBTYPE_BOOL`||関数が文字引数の長さなどのスカラー コンテンツを返す場合は `FALSE`、ヒストグラム テーブルなどのテーブルを返す場合は `TRUE` になります。|  
|`DESCRIPTION`|`DBTYPE_WSTR`||関数についてのわかりやすい説明。|  
|`HELP_FILE`|`DBTYPE_WSTR`||この関数のマニュアルを含んでいるファイルの名前。|  
|`HELP_CONTEXT`|`DBTYPE_I4`||この関数のヘルプ コンテキスト ID。|  
  
## <a name="restriction-columns"></a>制限の列  
 `DMSCHEMA_MINING_FUNCTIONS`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`SERVICE_NAME`|`DBTYPE_WSTR`|任意。|  
|`FUNCTION_NAME`|`DBTYPE_WSTR`|任意。|  
  
## <a name="see-also"></a>参照  
 [データ マイニング スキーマ行セット](../../schema-rowsets/data-mining/data-mining-schema-rowsets.md) 
  
  
