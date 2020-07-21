---
title: MSSQLSERVER_17887 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17887 (Database Engine error)
ms.assetid: ad0806e6-3296-4c32-b103-fccf0f8a8d3d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cdd998fdf93b12f58022ff345c8ea781f368d068
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780709"
---
# <a name="mssqlserver_17887"></a>MSSQLSERVER_17887
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
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
  
