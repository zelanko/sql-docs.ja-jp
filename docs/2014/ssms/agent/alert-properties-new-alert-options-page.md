---
title: '[警告のプロパティ]: [新しい警告] ([オプション] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.alert.options.f1
ms.assetid: 6e4f41aa-832d-46ba-b6b5-cf1d3b15d33f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 69f467af1c797b9bf1cfa55c7def8456ad4a32bd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63061276"
---
# <a name="alert-properties-new-alert-options-page"></a>[警告のプロパティ]:[新しい警告] ([オプション] ページ)
  このページを使用すると、エージェントの[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]警告のオプションを表示および変更できます。  
  
## <a name="options"></a>オプション  
 **メッセージ**  
 イベントからのエラー テキストがある場合は、それを電子メール通知に含めます。  
  
 **ポケット**  
 イベントからのエラー テキストがある場合は、それをポケットベル通知に含めます。  
  
 **Net send**  
 イベントからのエラー テキストがある場合は、それを Net Send 通知に含めます。  
  
 **[送信する付加通知メッセージ]**  
 通知メッセージに含める追加のテキストを入力します。  
  
 **[応答の遅延]**  
 反復的に発生するイベントの遅延を指定します。 イベントの中には、短時間に頻繁に発生するものがあります。 そのようなイベントに対しては、その発生を認識するだけで、すべてのイベントについて応答を返さないようにする場合があります。 このオプションを使用して、タイムアウトを指定します。遅延が発生すると、警告がイベントに応答し[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]た後、エージェントは、イベントが遅延中に発生したかどうかに関係なく、指定された遅延を待機してからもう一度応答します。  
  
 **分**  
 遅延を分単位で指定します。 イベントが発生するごとに応答するには、0 分 0 秒を指定します。  
  
 **Seconds**  
 遅延を秒単位で指定します。 イベントが発生するごとに応答するには、0 分 0 秒を指定します。  
  
## <a name="see-also"></a>参照  
 [アラート](alerts.md)  
  
  
