---
title: MSSQLSERVER_41365 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41365 (Database Engine error)
ms.assetid: 4fc7ec15-b722-4e3d-b7f9-3d39d171e96e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f20150add2b407c6ef2625a08a28a4f0e036b6de
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551360"
---
# <a name="mssqlserver_41365"></a>MSSQLSERVER_41365
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|41365|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|HK_MERGE_SCHEDULE_ERROR|  
|メッセージ テキスト|データベース %.*ls のトランザクション範囲 [%ld, %ld] に対するマージ要求がスケジュールされませんでした。 範囲を表すチェックポイント ファイルは、マージに使用できないか、実行中のマージの一部です。|  
  
## <a name="explanation"></a>説明  
 範囲を表すチェックポイント ファイルは、マージに使用できないか、実行中のマージの一部です。  
  
## <a name="user-action"></a>ユーザーの操作  
 同じ要求を再度発行する前に、マージ/待機にもっと適したトランザクション範囲を指定します。 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
