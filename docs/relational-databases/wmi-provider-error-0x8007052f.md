---
title: "WMI エラー 0x8007052f | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: 0x8007052f (WMI error)
ms.assetid: a33f12bd-15c4-42a8-b343-de44c3e87729
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 050f4c13d5c7c5f232cca65dd38dbcfcdb27c5bb
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="wmi-provider-error-0x8007052f"></a>WMI プロバイダー エラー 0x8007052f
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|0x8007052f|  
|イベント ソース|WMI プロバイダー エラー|  
|コンポーネント|SQL Server 構成マネージャー|  
|シンボル名|NA|  
|メッセージ テキスト|ログオン失敗: ユーザー アカウントの制限。 考えられる原因として、空のパスワードが許可されていない、ログオン時間制限、またはポリシーによる制限が適用されたことなどが挙げられます。|  
  
## <a name="explanation"></a>説明  
 このエラーは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が Windows Server クラスターまたは Windows Server ドメイン コントローラー上で実行されているときに、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成マネージャーを使用してビルトイン アカウント (Network Service、Local Service、または Local System) に切り替えると発生する場合があります。 Windows Server クラスターまたは Windows Server ドメイン コントローラー上では、ビルトイン アカウントでサービスを実行しないでください。 サービス アカウントに関する推奨事項については、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オンライン ブックの「Windows サービス アカウントの設定」を参照してください。  
  
## <a name="user-action"></a>ユーザーの操作  
 ドメイン アカウントを使用するように [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を構成します。  
  
  
