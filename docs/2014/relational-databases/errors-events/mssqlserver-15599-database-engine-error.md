---
title: MSSQLSERVER_15599 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 15599 (Database Engine error)
ms.assetid: 97e427a9-8587-46ea-954b-974b5df9c223
caps.latest.revision: 8
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 3678e5d075d4d81481aa0e814f85a1de4ad99009
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177996"
---
# <a name="mssqlserver15599"></a>MSSQLSERVER_15599
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|15599|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SEC_LOCAL_TEMP_AUDIT_PERMISSIONS|  
|メッセージ テキスト|監査と権限をローカルの一時オブジェクトで設定できません。|  
  
## <a name="explanation"></a>説明  
 監査と権限は、ローカルまたはグローバルの一時オブジェクトに設定する場合にまったく影響しません。 このステートメントではエラーは発生しません (操作は成功を返します) が、効果はありません。  
  
 この動作は変更されていませんが、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降はこの情報メッセージがユーザーに通知されます。  
  
## <a name="user-action"></a>ユーザーの操作  
 操作は必要ありませんが、ローカルまたはグローバルの一時オブジェクトに監査または権限を設定するステートメントを削除することを検討してください。  
  
  