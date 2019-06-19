---
title: MSSQLSERVER_15661 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 15661 (Database Engine error)
ms.assetid: 88b01bfb-74ce-4aa0-aec0-7885261c7ef3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0271487ec01b29afe5485f754628d20fa4f74322
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62858926"
---
# <a name="mssqlserver15661"></a>MSSQLSERVER_15661
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
