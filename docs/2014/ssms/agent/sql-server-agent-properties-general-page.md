---
title: '[SQL Server エージェントのプロパティ] ([全般] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.general.f1
ms.assetid: b51601e9-5454-43c6-bb5e-24eb2ff043c8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 667a07744acf4b6d8b0dfa1e83adca738add0b4f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058704"
---
# <a name="sql-server-agent-properties-general-page"></a>[SQL Server エージェントのプロパティ] ([全般] ページ)
  このページを使用すると、エージェントサービスの全般プロパティを表示および変更 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] できます。  
  
## <a name="options"></a>オプション  
 **サービスの状態**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスの現在の状態を表示します。  
  
 **[予期しない停止時に SQL Server を自動的に再起動する]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が予期せず停止した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再起動します。  
  
 **[予期しない停止時に SQL Server エージェントを自動的に再起動する]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが予期せず停止した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを再起動します。  
  
 **/Db**  
 エラー ログのファイル名を指定します。  
  
 **...**  
 エラー ログ ファイルを参照します。  
  
 **[実行トレース メッセージを含める]**  
 エラー ログに実行トレース メッセージを含めます。 トレース メッセージにより、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの処理に関する詳細情報が得られます。 そのため、このオプションを選択した場合は、ログ ファイルに必要なディスク領域が大きくなります。 このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントに関係すると思われる問題をトラブルシューティングするときにのみ選択してください。  
  
 **[OEM ファイルに書き込む]**  
 エラー ログ ファイルを非 Unicode ファイルとして書き込みます。 これにより、ログ ファイルによって消費されるディスク領域が減少します。 ただし、このオプションを有効にすると Unicode データを含むメッセージが読み取りにくくなる場合があります。  
  
 **[Net Send 受信者]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによってログ ファイルに書き込まれるメッセージの、Net Send 通知を受信するオペレーターの名前を入力します。  
  
## <a name="see-also"></a>参照  
 [通信](operators.md)   
 [SQL Server エージェント エラー ログ](sql-server-agent-error-log.md)  
  
  
