---
title: "[警告のプロパティ] - [新しい警告] ([オプション] ページ) | Microsoft Docs"
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
- sql13.ag.alert.options.f1
ms.assetid: 6e4f41aa-832d-46ba-b6b5-cf1d3b15d33f
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 360fc93c7f1e8cf7194637b7f5cffb20cb772c3c
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="alert-properties---new-alert-options-page"></a>[警告のプロパティ] - [新しい警告] \([オプション] ページ)
このページを使用すると、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの警告のオプションを表示および変更できます。  
  
## <a name="options"></a>オプション  
**電子メール**  
イベントからのエラー テキストがある場合は、それを電子メール通知に含めます。  
  
**ポケットベル**  
イベントからのエラー テキストがある場合は、それをポケットベル通知に含めます。  
  
**[Net Send]**  
イベントからのエラー テキストがある場合は、それを Net Send 通知に含めます。  
  
**[送信する付加通知メッセージ]**  
通知メッセージに含める追加のテキストを入力します。  
  
**[応答の遅延]**  
反復的に発生するイベントの遅延を指定します。 イベントの中には、短時間に頻繁に発生するものがあります。 そのようなイベントに対しては、その発生を認識するだけで、すべてのイベントについて応答を返さないようにする場合があります。 このオプションは、タイムアウトを指定するために使用します。 遅延を指定した場合、イベントに対して警告が返された後、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントは、イベントが遅延中に発生するかどうかに関係なく、再び応答するまでに指定の遅延を待ちます。  
  
**Minutes**  
遅延を分単位で指定します。 イベントが発生するごとに応答するには、0 分 0 秒を指定します。  
  
**Seconds**  
遅延を秒単位で指定します。 イベントが発生するごとに応答するには、0 分 0 秒を指定します。  
  
## <a name="see-also"></a>参照  
[警告](../../ssms/agent/alerts.md)  
  

