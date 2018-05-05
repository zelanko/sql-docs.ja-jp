---
title: CREATE INDEX ステートメント |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CREATE INDEX [ODBC]
- SQL grammar [ODBC], create index
ms.assetid: 69438247-eef3-44c5-bef2-acef4e146f41
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 86d4cf1bb047cd475b86b9a58c37f3268c07c91d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="create-index-statement"></a>CREATE INDEX ステートメント
CREATE INDEX ステートメントの構文です。  
  
 [一意] インデックスの作成*インデックス名*ON*テーブル名*(*列識別子*[ASC] [DESC] [、*列識別子*[ASC][DESC]...])\<*インデックスのオプションの一覧*>  
  
 ここで\<*インデックスのオプションの一覧*> を指定できます: プライマリ&#124;NULL を許可しないように&#124;IGNORE NULL  
  
 Microsoft Access ドライバーだけでは、NULL を許可しないようにし、NULL を無視するインデックスのオプションを使用します。 DBASE および Paradox ドライバー、構文を受け付けるが、いずれかのオプションの存在を無視します。  
  
 Paradox ドライバーを使用する場合、CREATE INDEX ステートメントは、Paradox キー ファイルのプライマリとセカンダリ ファイルを作成します。  
  
 このステートメントは、Microsoft Excel またはテキストのドライバーでサポートされていません。
