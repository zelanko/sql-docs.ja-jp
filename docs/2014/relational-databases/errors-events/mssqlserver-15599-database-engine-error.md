---
title: MSSQLSERVER_15599 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15599 (Database Engine error)
ms.assetid: 97e427a9-8587-46ea-954b-974b5df9c223
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 99892d5d7ca9bcec5648388072aec0acf557111d
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84969512"
---
# <a name="mssqlserver_15599"></a>MSSQLSERVER_15599
    
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
  
  
