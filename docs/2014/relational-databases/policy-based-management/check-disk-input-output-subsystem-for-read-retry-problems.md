---
title: ディスク入出力サブシステム読み取り再試行の問題の確認 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: cedf4097-5b73-4964-9935-74a101847019
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ebc6dc1c178eec55bbc635ada7c1fffa6873cd0d
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "43814118"
---
# <a name="check-disk-input-output-subsystem-for-read-retry-problems"></a>ディスク I/O サブシステムの読み取り再試行の問題の確認
  このルールでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のイベント ログにエラー メッセージ 825 があるどうかを確認します。 このメッセージは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が最初の試行ではディスクからデータを読み取れなかったことを示します。 このメッセージは、ディスク I/O サブシステムに大きな問題があることを示しています。 このメッセージは、現時点では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の問題を示していませんが、 ディスクの問題を解決しないと、データの損失やデータベースの破損につながる可能性があります。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 次の操作を行って、原因となっているハードウェアの問題を特定し、解決してください。  
  
-   このメッセージのエラー ログと変数テキストを確認し、問題の原因を明らかにする手掛かりを見つける。  
  
-   ディスク システムを確認する。 この問題は、ディスク、ディスク コントローラー、アレイ カード、またはディスク ドライバーに関連している可能性があります。  
  
-   ディスク システムの状態を調べる最新のユーティリティがあるかどうか、ディスクの製造元に問い合わせる。  
  
-   ドライバーの最新の更新があるかどうか、ディスクの製造元に問い合わせる。  
  
## <a name="for-more-information"></a>詳細情報  
 [MSSQLSERVER_825](../errors-events/mssqlserver-825-database-engine-error.md)  
  
 [SQL Server I/O Basics, Chapter 2](http://go.microsoft.com/fwlink/?linkid=69370)  
  
  
