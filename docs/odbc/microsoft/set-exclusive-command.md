---
title: "SET 排他コマンド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SET EXCLUSIVE command [ODBC]
ms.assetid: d4fe12c5-7e8b-4d20-9ea4-2bcaffb271f2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 830cec1dbb87ae2bc4336d28d6112fd76b4db0ed
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="set-exclusive-command"></a>排他の SET コマンド
テーブルのファイルが、ネットワーク上の排他的 or 共有の使用に開かれるかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SET EXCLUSIVE ON | OFF  
```  
  
## <a name="arguments"></a>引数  
 ON  
 開いたユーザーにネットワークに開かれたテーブルへのアクセスを制限します。 テーブルに、ネットワーク上の他のユーザーにアクセスできません。 SET 排他 ON では、読み取り専用でアクセスすることが他のすべてのユーザーを防ぐことができます。  
  
 OFF  
 (ドライバーの既定の Visual FoxPro の既定値は ON のグローバル データのセッションと OFF のプライベート データ セッションです。)共有しても、ネットワーク上のすべてのユーザーによって変更するネットワークに開かれたテーブルを使用します。  
  
## <a name="remarks"></a>解説  
 排他的な設定の設定を変更する前に開かれたテーブルの状態は変更されません。 たとえば、排他設定は、後で変更を OFF に設定排他 ON に設定と、テーブルが開いている場合、テーブルには、排他的な使用状態が保持されます。  
  
## <a name="see-also"></a>参照  
 [ODBC Visual FoxPro セットアップ ダイアログ ボックス](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)
