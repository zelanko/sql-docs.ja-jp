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
ms.openlocfilehash: 4fe84a470f5e877c73701168394cd85d75253fb7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67997760"
---
# <a name="set-blocksize-command"></a>SET BLOCKSIZE コマンド
メモフィールドを格納するためのディスク領域の割り当て方法を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET BLOCKSIZE TO nBytes  
```  
  
## <a name="arguments"></a>引数  
 *nBytes*  
 メモフィールドのディスク領域を割り当てるブロックサイズを指定します。 *Nbytes*が0の場合、ディスク領域は1バイト (1 バイトのブロック) で割り当てられます。 *Nbytes*が 1 ~ 32 の整数である場合、ディスク領域は*nbytes*バイトに512を掛けたブロックで割り当てられます。 *Nbytes*が32より大きい場合は、 *nbytes*バイトのブロックにディスク領域が割り当てられます。 32より大きいブロックサイズの値を指定した場合は、大量のディスク領域を節約できます。  
  
## <a name="remarks"></a>解説  
 SET BLOCKSIZE の既定値は64です。 ファイルの作成後にブロックサイズを別の値にリセットするには、新しい値に設定してから、COPY を使用して新しいテーブルを作成します。 新しいテーブルには、指定されたブロックサイズがあります。
