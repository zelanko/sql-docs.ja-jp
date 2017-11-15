---
title: MSSQLSERVER_50000 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: 50000 [SQL Server Native Client setup error]
ms.assetid: 5426d87a-d5d9-4984-b211-b07d69e834a2
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 84f6e861c63326b2fd972d987bb45fa56635fd0f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-native-client-error-mssqlserver50000"></a>SQL Server Native Client エラー MSSQLSERVER_50000
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|製品バージョン|11.0|  
|イベント ID|50000|  
|イベント ソース|SETUP|  
|コンポーネント|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client|  
|シンボル名||  
|メッセージ テキスト|ファイル '%.*ls' の読み取り中にネットワーク エラーが発生しました。|  
  
## <a name="explanation"></a>説明  
 名前が sqlncli.msi から変更された MSI ファイルを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client がインストールされているコンピューターで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client をインストール (または更新) しようとしました。  
  
## <a name="user-action"></a>ユーザーの操作  
 このエラーを解決するには、既存のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client をアンインストールします。 このエラーを防ぐには、sqlncli.msi 以外の名前の MSI ファイルから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client をインストールしないようにします。  
  
## <a name="internal-only"></a>内部使用のみ  
  
