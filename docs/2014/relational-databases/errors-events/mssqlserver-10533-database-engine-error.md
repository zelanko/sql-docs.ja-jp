---
title: MSSQLSERVER_10533 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10533 (Database Engine error)
ms.assetid: cc2fbdab-7b90-415f-a1f9-066824344283
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ccef25bc8f594cb6ea0b60aefab838ef27cda6f8
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84969792"
---
# <a name="mssqlserver_10533"></a>MSSQLSERVER_10533
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|10533|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|PG_NAME_TOO_BIG|  
|メッセージ テキスト|プラン ガイド '%.*ls' を作成できません。プラン ガイドの名前が最大長である 124 文字を超えています。 124 文字以下の名前を指定します。|  
  
## <a name="explanation"></a>説明  
 プラン ガイドの名前が最大長である 124 文字を超えています。  
  
## <a name="user-action"></a>ユーザーの操作  
 124 文字以下の名前を指定します。  
  
## <a name="see-also"></a>参照  
 [プランガイド](../performance/plan-guides.md)   
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql)  
  
  
