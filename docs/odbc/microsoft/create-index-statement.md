---
title: CREATE INDEX ステートメント |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE INDEX [ODBC]
- SQL grammar [ODBC], create index
ms.assetid: 69438247-eef3-44c5-bef2-acef4e146f41
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ad15ad436b0f34f00acbd75e371e998183f22d2f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081907"
---
# <a name="create-index-statement"></a>CREATE INDEX ステートメント
CREATE INDEX ステートメントの構文は次のとおりです。  
  
 CREATE [UNIQUE] インデックス*インデックス-名前*に*テーブル名*(*列識別子*[asc] [desc] [,*列識別子*[asc] [desc]...])\<*インデックスオプションリスト*付き>  
  
 ここ\<で、*インデックスオプションリスト*> にできます。 PRIMARY &#124; null を許可しない &#124; null を無視する  
  
 [NULL を許可しない] および [NULL インデックスを無視する] オプションは、Microsoft Access ドライバーでのみ使用されます。 DBASE および Paradox ドライバーは構文を受け入れますが、どちらのオプションも存在しません。  
  
 Paradox ドライバーを使用すると、CREATE INDEX ステートメントによって、Paradox のプライマリキーファイルとセカンダリファイルが作成されます。  
  
 このステートメントは、Microsoft Excel またはテキストドライバーではサポートされていません。
