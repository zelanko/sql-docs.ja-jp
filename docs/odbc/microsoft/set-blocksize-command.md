---
title: SET BLOCKSIZE コマンド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- set blocksize command [ODBC]
ms.assetid: 0c11580f-37f5-4a8e-99be-9fb9c44bb433
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8e2fe90c50d87cea5b949787a6504479c2670e14
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="set-blocksize-command"></a>SET BLOCKSIZE コマンド
メモ フィールドを格納するためのディスク領域の割り当て方法を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET BLOCKSIZE TO nBytes  
```  
  
## <a name="arguments"></a>引数  
 *nBytes*  
 メモ フィールド用のディスク領域が割り当てられているブロック サイズを指定します。 場合*nBytes*は 0、1 バイト (1 バイトのブロック) でディスク領域が割り当てられます。 場合*nBytes*は 1 から 32、ディスク領域の間の整数がのブロックで割り当てられている*nBytes*バイト数を掛けた 512 です。 場合*nBytes*が 32 を超えるのブロックで割り当てられているディスク領域*nBytes*バイトです。 32 を超えるブロック サイズの値を指定する場合は、大量のディスク容量を節約できます。  
  
## <a name="remarks"></a>解説  
 ブロック サイズの設定の既定値は 64 です。 ファイルが作成された後、別の値に、ブロック サイズをリセットするに新しい値に設定し、コピーを使用して、新しいテーブルを作成します。 新しいテーブルには、指定されたブロック サイズがあります。
