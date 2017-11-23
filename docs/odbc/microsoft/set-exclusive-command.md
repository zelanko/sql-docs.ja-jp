---
title: "SET 排他コマンド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SET EXCLUSIVE command [ODBC]
ms.assetid: d4fe12c5-7e8b-4d20-9ea4-2bcaffb271f2
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f5aa039c9af4b3dfbabce2647408be7f612c80f3
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
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
