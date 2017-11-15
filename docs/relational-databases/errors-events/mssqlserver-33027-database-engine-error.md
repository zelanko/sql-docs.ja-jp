---
title: MSSQLSERVER_33027 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 33027 (Database Engine error)
ms.assetid: bfdc626e-7958-4511-987d-3b687824e8af
caps.latest.revision: "11"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 5a80585e89feccfe23af6f33576e6acf8fa8e635
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver33027"></a>MSSQLSERVER_33027
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|33027|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SEC_CRYPTOPROV_CANTLOADDLL|  
|メッセージ テキスト|Authenticode 署名またはファイル パスが無効なため、暗号プロバイダー '%.*ls' を読み込めませんでした。 前のメッセージでその他のエラーを確認してください。|  
  
## <a name="explanation"></a>説明  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、エラー メッセージに表示されている暗号化サービス プロバイダーを使用できませんでした。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が該当する DLL を読み込めなかったことが原因です。 名前が無効であるか、Authenticode 署名が無効です。  
  
## <a name="user-action"></a>ユーザーの操作  
このファイルが存在し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がファイルの場所にアクセスするための権限を持っていることを確認します。 エラー ログで、その他の関連メッセージを確認します。 または、暗号化サービス プロバイダーに詳細を問い合わせてください。  
  
