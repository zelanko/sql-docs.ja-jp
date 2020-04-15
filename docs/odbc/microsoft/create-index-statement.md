---
title: インデックス ステートメントの作成 |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280972"
---
# <a name="create-index-statement"></a>CREATE INDEX ステートメント
CREATE INDEX ステートメントの構文は次のとおりです。  
  
 *テーブル名*に [UNIQUE] インデックス*名*を作成します (*列識別子*[ASC][DESC],*列識別子*[ASC][DESC.]]WITH \<*インデックスオプションリスト*>  
  
 \<*インデックス オプション リスト*>できる場所: プライマリ &#124; DISALLOW NULL &#124; IGNORE NULL  
  
 DISALLOW NULL と IGNORE NULL インデックス オプションを使用するのは、Access ドライバーだけです。 dBASE と Paradox ドライバーは構文を受け入れますが、どちらのオプションも無視します。  
  
 Paradox ドライバを使用すると、CREATE INDEX ステートメントによって、Paradox プライマリ キー ファイルとセカンダリ ファイルが作成されます。  
  
 このステートメントは、Excel またはテキスト ドライバーではサポートされていません。
