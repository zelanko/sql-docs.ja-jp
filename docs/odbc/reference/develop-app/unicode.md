---
title: ユニコード |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC]
- Unicode [ODBC], about Unicode
ms.assetid: 113e1c9a-8333-4805-86f2-e4b57ab816a5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9824e76cebabb6f5f84505292801a0094e359f0f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302448"
---
# <a name="unicode"></a>Unicode
Unicode では、多くの言語で文字のエンコーディングが定義されています。  
  
 Unicode 規格の詳細については、「[ユニコード コンソーシアム](https://www.unicode.org)」を参照してください。  
  
 ユニコードは、ユニバーサル文字セットを定義します。 Windows ANSI コード ページは、通常 1 つの言語の文字を含む文字セットを定義します。 異なるコード ページを使用する必要があるアプリケーションを作成することがより困難な場合があります。  
  
 Unicode はコード ページを必要としません。 すべてのコード ポイントは、ある言語の 1 つの文字にマップされます。  
  
 現在、ODBC がサポートする Unicode エンコードは UCS-2 で、16 ビット整数 (固定長) を使用して文字を表します。 Unicode を使用すると、アプリケーションは異なる言語で動作できます。  
  
 ODBC 3.5 (またはそれ以降) のドライバー マネージャーは、Unicode 対応です。 これは、関数呼び出しと文字列データ型という 2 つの主要な領域に影響します。 ドライバー マネージャーは、アプリケーションとドライバーの要求に応じて、関数の文字列引数と文字列データをマップします。 これらの 2 つの領域については[、「Unicode 関数の引数](../../../odbc/reference/develop-app/unicode-function-arguments.md)」と[「Unicode データ](../../../odbc/reference/develop-app/unicode-data.md)」のセクションで詳しく説明します。  
  
 ODBC 3.5 (またはそれ以降) ドライバー マネージャーは、Unicode アプリケーションと ANSI アプリケーションの両方で Unicode ドライバーの使用をサポートします。 また、ANSI アプリケーションで ANSI ドライバーを使用することもできます。 ドライバー マネージャーは、ANSI ドライバーを使用して作業する Unicode アプリケーションの限定された Unicode から ANSI へのマッピングを提供します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [Unicode 関数の引数](../../../odbc/reference/develop-app/unicode-function-arguments.md)  
  
-   [Unicode データ](../../../odbc/reference/develop-app/unicode-data.md)
