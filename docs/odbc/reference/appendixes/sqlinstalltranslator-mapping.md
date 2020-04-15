---
title: SQL インストールトランスレータ マッピング |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLInstallTranslator function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLInstallTranslator
ms.assetid: bcd9ba4f-7834-4bc4-876e-c7478998e524
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8ab5ebccaac7ccf6374971c1d21040ad15fb3e55
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300584"
---
# <a name="sqlinstalltranslator-mapping"></a>SQLInstallTranslator のマッピング
ODBC *2.x*アプリケーションが ODBC *3.x*ドライバを使用して**SQLInstallTranslator**を呼び出すと、ドライバ マネージャは呼び出しを**SQLInstallTranslatorEx**にマップします。アプリケーションは、*引数 lpszInfFile*を NULL 以外の値に設定した ODBC *3.x*ドライバー マネージャーで**SQLInstallTranslator**を呼び出すべきではありません。 ODBC。ODBC *2.x*で使用されている INF ファイルは、下位互換性を保つためにも ODBC *3.x*ではサポートされなくなりました。
