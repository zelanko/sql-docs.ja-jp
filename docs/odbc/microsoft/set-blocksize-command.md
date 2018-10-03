---
title: SET BLOCKSIZE コマンド |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e904d341513047b3940cf5b3fc2ba9538cdb5c8f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47764230"
---
# <a name="set-blocksize-command"></a>SET BLOCKSIZE コマンド
メモ フィールドの記憶域のディスク領域の割り当て方法を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET BLOCKSIZE TO nBytes  
```  
  
## <a name="arguments"></a>引数  
 *nBytes*  
 メモ フィールドのディスク領域の割り当てをブロック サイズを指定します。 場合*nBytes*は 0、1 バイト (1 バイトのブロック) でディスク領域が割り当てられます。 場合*nBytes*でのブロック 1 と、32 のディスク領域の間の整数の割り当ては*nBytes* 512 バイトを乗算します。 場合*nBytes*が 32 を超えるディスク領域の割り当てのブロックで*nBytes*バイト。 32 を超えるブロック サイズの値を指定する場合は、大量のディスク領域を節約できます。  
  
## <a name="remarks"></a>コメント  
 ブロック サイズの設定の既定値は、64 です。 ファイルが作成された後は、別の値にブロック サイズをリセットするには、新しい値を設定して、コピーを使用して、新しいテーブルを作成します。 新しいテーブルには、指定されたブロック サイズがあります。
