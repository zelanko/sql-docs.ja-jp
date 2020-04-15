---
title: ブロックサイズの設定コマンド |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set blocksize command [ODBC]
ms.assetid: 0c11580f-37f5-4a8e-99be-9fb9c44bb433
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3eb9fbe9df90f7ddafebc6baa029164a578a6da3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300902"
---
# <a name="set-blocksize-command"></a>SET BLOCKSIZE コマンド
メモフィールドの格納にディスク領域を割り当てる方法を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET BLOCKSIZE TO nBytes  
```  
  
## <a name="arguments"></a>引数  
 *Nbytes*  
 メモフィールドのディスク・スペースを割り振るブロック・サイズを指定します。 *nBytes が*0 の場合、ディスク領域は 1 バイト (1 バイトのブロック) で割り当てられます。 *nBytes が*1 から 32 までの整数の場合、ディスク領域は*nBytes*バイトのブロックに 512 を掛けた単位で割り当てられます。 *nBytes が*32 より大きい場合、ディスク領域は*nBytes*バイトのブロック単位で割り振られます。 ブロック サイズの値が 32 より大きい場合は、ディスク領域を大幅に節約できます。  
  
## <a name="remarks"></a>解説  
 SET ブロックサイズのデフォルト値は 64 です。 ファイルの作成後にブロック サイズを別の値にリセットするには、ブロック サイズを新しい値に設定し、COPY を使用して新しいテーブルを作成します。 新しいテーブルのブロック サイズが指定されています。
