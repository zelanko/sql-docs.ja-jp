---
title: MSSQLSERVER_41333 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: acf61c82e7ca67172843c33d5ec5cef3165ccffa
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37419912"
---
# <a name="mssqlserver41333"></a>MSSQLSERVER_41333
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|41333|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|CROSS_CONTAINER_ISOLATION_FAILURE|  
|メッセージ テキスト|RepeatableRead トランザクション、Serializable トランザクション、および RepeatableRead または Serializable 分離でメモリ最適化されていないテーブルにアクセスするトランザクションでは、スナップショット分離を使用したうえでメモリ最適化テーブルおよびネイティブ コンパイル ストアド プロシージャにアクセスする必要があります。|  
  
## <a name="explanation"></a>説明  
 ディスク ベース トランザクションと XTP トランザクションの間の分離レベルが高いユーザーに対しては、制約があります。  
  
## <a name="user-action"></a>ユーザーの操作  
 メモリ最適化テーブル (およびネイティブ コンパイル プロシージャ) とディスク ベース テーブルでは、高レベルの分離操作を実行しないでください。  
  
 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
