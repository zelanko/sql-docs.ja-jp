---
title: ユニークコマンドを設定する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET UNIQUE command [ODBC]
ms.assetid: 1f69e31e-4599-47cc-ac89-b86fba8703c5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7d3d37509450d1305891100b37bfd1ad026166e8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300842"
---
# <a name="set-unique-command"></a>SET UNIQUE コマンド
インデックス キー値が重複しているレコードをインデックス ファイルに保持するかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET UNIQUE ON | OFF  
```  
  
## <a name="arguments"></a>引数  
 ON  
 重複するインデックス キー値を持つレコードをインデックス ファイルに含まないことを指定します。 元のインデックス キー値を持つ最初のレコードのみがインデックス ファイルに含まれます。  
  
 OFF  
 (デフォルト)。インデックス キー値が重複しているレコードをインデックス ファイルに含めるかどうかを指定します。  
  
## <a name="remarks"></a>解説  
 インデックス ファイルは、REINDEX を発行するときに SET UNIQUE 設定を保持します。 詳細については[、INDEX](../../odbc/microsoft/index-command.md)を参照してください。
