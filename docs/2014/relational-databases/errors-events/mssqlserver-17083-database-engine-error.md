---
title: MSSQLSERVER_17083 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 17083 (Database Engine error)
ms.assetid: 6c83737d-0531-4fd9-88f6-2da5a150532d
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: de02c912edc8af455f6615524be967a000715235
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37419281"
---
# <a name="mssqlserver17083"></a>MSSQLSERVER_17083
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|17083|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|P3_HEKATON_NOT_ATOMIC|  
|メッセージ テキスト|ネイティブ コンパイル ストアド プロシージャの本体は ATOMIC ブロックである必要があります。|  
  
## <a name="explanation"></a>説明  
 ネイティブ コンパイル ストアド プロシージャの本体に ATOMIC ブロックがありませんでした。  
  
## <a name="user-action"></a>ユーザーの操作  
 ネイティブ コンパイル ストアド プロシージャには ATOMIC ブロックが必要です。 以下に例を示します。  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE= N’us_english’)  
```  
  
 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
