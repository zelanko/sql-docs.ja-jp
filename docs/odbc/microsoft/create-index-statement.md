---
title: "CREATE INDEX ステートメント |Microsoft ドキュメント"
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
helpviewer_keywords:
- CREATE INDEX [ODBC]
- SQL grammar [ODBC], create index
ms.assetid: 69438247-eef3-44c5-bef2-acef4e146f41
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6737ad2bdde9516291863214d3da5dd6087e3ec2
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="create-index-statement"></a>CREATE INDEX ステートメント
CREATE INDEX ステートメントの構文です。  
  
 [一意] インデックスの作成*インデックス名*ON*テーブル名*(*列識別子*[ASC] [DESC] [、*列識別子*[ASC][DESC]...])\<*インデックスのオプションの一覧*>  
  
 ここで\<*インデックスのオプションの一覧*> を指定できます: プライマリ &#124;です。NULL &#124; を許可しません。NULL を無視します。  
  
 Microsoft Access ドライバーだけでは、NULL を許可しないようにし、NULL を無視するインデックスのオプションを使用します。 DBASE および Paradox ドライバー、構文を受け付けるが、いずれかのオプションの存在を無視します。  
  
 Paradox ドライバーを使用する場合、CREATE INDEX ステートメントは、Paradox キー ファイルのプライマリとセカンダリ ファイルを作成します。  
  
 このステートメントは、Microsoft Excel またはテキストのドライバーでサポートされていません。
