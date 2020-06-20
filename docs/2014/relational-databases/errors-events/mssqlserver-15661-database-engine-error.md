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
ms.openlocfilehash: 966e23e8d970c36eba81253228cc18ed4af3ff77
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84969492"
---
# <a name="mssqlserver_15661"></a>MSSQLSERVER_15661
    
## <a name="details"></a>詳細  
  
|||  
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
  
  
