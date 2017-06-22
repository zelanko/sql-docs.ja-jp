---
title: "[SQL Server エージェントのプロパティ] ([全般] ページ) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ag.agent.general.f1
ms.assetid: b51601e9-5454-43c6-bb5e-24eb2ff043c8
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4da1f93dcc4c6e75b554a1a6dab8cbeb86096009
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-agent-properties-general-page"></a>[SQL Server エージェントのプロパティ] ([全般] ページ)
このページを使用すると、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスの全般プロパティを表示したり、変更したりできます。  
  
## <a name="options"></a>オプション  
**[サービスの状態]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスの現在の状態を表示します。  
  
**[予期しない停止時に SQL Server を自動的に再起動する]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] が予期せず停止した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] を再起動します。  
  
**[予期しない停止時に SQL Server エージェントを自動的に再起動する]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントが予期せず停止した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントを再起動します。  
  
**Filename**  
エラー ログのファイル名を指定します。  
  
**[[...]]**  
エラー ログ ファイルを参照します。  
  
**[実行トレース メッセージを含める]**  
エラー ログに実行トレース メッセージを含めます。 トレース メッセージにより、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの処理に関する詳細情報が得られます。 そのため、このオプションを選択した場合は、ログ ファイルに必要なディスク領域が大きくなります。 このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントに関係すると思われる問題をトラブルシューティングするときにのみ選択してください。  
  
**[OEM ファイルに書き込む]**  
エラー ログ ファイルを非 Unicode ファイルとして書き込みます。 これにより、ログ ファイルによって消費されるディスク領域が減少します。 ただし、このオプションを有効にすると Unicode データを含むメッセージが読み取りにくくなる場合があります。  
  
**[Net Send 受信者]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントによってログ ファイルに書き込まれるメッセージの、Net Send 通知を受信するオペレーターの名前を入力します。  
  
## <a name="see-also"></a>参照  
[演算子](../../ssms/agent/operators.md)  
[SQL Server エージェント エラー ログ](../../ssms/agent/sql-server-agent-error-log.md)  
  

