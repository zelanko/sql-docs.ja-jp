---
title: MSSQLSERVER_17887 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 17887 (Database Engine error)
ms.assetid: ad0806e6-3296-4c32-b103-fccf0f8a8d3d
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 30fe23973966927471bc21cb484b81ae9636e842
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425991"
---
# <a name="mssqlserver17887"></a>MSSQLSERVER_17887
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|17887|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SRV_IO_COMP_LISTENER_NONYIELDING|  
|メッセージ テキスト|IO 完了リスナー (0x%lx) のワーカー 0x%p が、ノード %ld で応答を停止している可能性があります。 CPU の概算使用量: カーネル %I64d ミリ秒、ユーザー %I64d ミリ秒、間隔: %I64d。|  
  
## <a name="explanation"></a>説明  
 ネットワークの読み取りまたは書き込みのイベント用に I/O 完了ルーチンを実行しているときに、指定されたノード上の I/O 完了ポート リスナーに問題が発生している可能性があることを示します。 I/O 完了ポート リスナーが I/O 完了ルーチンの実行から戻ると、このエラーは解決します。  
  
## <a name="user-action"></a>ユーザーの操作  
 マイクロソフト カスタマー サポート サービス (CSS) に連絡してください。  
  
  
