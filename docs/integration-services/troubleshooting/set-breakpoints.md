---
title: "[ブレークポイントの設定] | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.setbreakpoints.f1"
helpviewer_keywords: 
  - "[ブレークポイントの設定] ダイアログ ボックス"
ms.assetid: 876e61b7-875c-43f4-bbce-d7eeb90f6730
caps.latest.revision: 24
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 24
---
# [ブレークポイントの設定]
  **[ブレークポイントの設定]** ダイアログ ボックスを使用すると、ブレークポイントを有効にしてブレークポイントの動作を制御するためのイベントを指定できます。  
  
## オプション  
 **有効**  
 選択すると、イベントのブレークポイントが有効になります。  
  
 **[ブレークの条件]**  
 ブレークポイントの設定に使用できるイベントの一覧を表示します。  
  
 **[ヒット カウントの種類]**  
 ブレークポイントがいつ有効になるかを指定します。  
  
|値|Description|  
|-----------|-----------------|  
|**毎回**|ブレークポイントにヒットすると、常に実行が中断されます。|  
|**ヒット カウント (等しい)**|ブレークポイントの発生回数がヒット カウントと等しくなると実行が中断されます。|  
|**[ヒット カウント (より大きいまたは等しい)]**|ブレークポイントの発生回数がヒット カウント以上になると実行が中断されます。|  
|**ヒット カウント (倍数)**|ヒット カウントの倍数だけブレークポイントが発生すると実行が中断されます。 たとえば、このオプションを 5 に設定すると、実行は 5 回ごとに中断されます。|  
  
 **[ヒット カウント]**  
 ブレークをトリガーするヒットの回数を指定します。 ブレークポイントが常に有効になっている場合、このオプションは使用できません。  
  
## 参照  
 [制御フローのデバッグ](../../integration-services/troubleshooting/debugging-control-flow.md)  
  
  