---
title: SET BLOCKSIZE コマンド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
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
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ee5b55501d055d3bea09903a5486e88de3cdc993
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
