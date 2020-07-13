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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c6aa512ff789fcbd00f45f84fb194d4ab3f5da07
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280972"
---
# <a name="create-index-statement"></a>CREATE INDEX ステートメント
CREATE INDEX ステートメントの構文は次のとおりです。  
  
 CREATE [UNIQUE] インデックス*インデックス-名前*に*テーブル名*(*列識別子*[asc] [desc] [,*列識別子*[asc] [desc]...])\<*インデックスオプションリスト*付き>  
  
 ここ\<で、*インデックスオプションリスト*> にできます。 PRIMARY &#124; null を許可しない &#124; null を無視する  
  
 [NULL を許可しない] および [NULL インデックスを無視する] オプションは、Microsoft Access ドライバーでのみ使用されます。 DBASE および Paradox ドライバーは構文を受け入れますが、どちらのオプションも存在しません。  
  
 Paradox ドライバーを使用すると、CREATE INDEX ステートメントによって、Paradox のプライマリキーファイルとセカンダリファイルが作成されます。  
  
 このステートメントは、Microsoft Excel またはテキストドライバーではサポートされていません。
