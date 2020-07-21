---
title: MSSQLSERVER_15661 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15661 (Database Engine error)
ms.assetid: 88b01bfb-74ce-4aa0-aec0-7885261c7ef3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9ad20f630056ac4e2f0fe37686955012c0239234
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553747"
---
# <a name="mssqlserver_15661"></a>MSSQLSERVER_15661
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|15661|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SQLErrorNum15661|  
|メッセージ テキスト|sp_estimate_data_compression_savings ストアド プロシージャは、一時テーブルに対しては使用できません。|  
  
## <a name="explanation"></a>説明  
 一時テーブルが sp_estimate_data_compression_savings ストアド プロシージャの引数に使用されました。 一時テーブルの圧縮はサポートされていますが、sp_estimate_data_compression_savings を使用して圧縮保存を推定することはできません。  
  
## <a name="user-action"></a>ユーザーの操作  
 sp_estimate_data_compression_savings の引数としての一時テーブルを削除します。  
  
  
