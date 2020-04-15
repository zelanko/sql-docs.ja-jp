---
title: SQL インストールトランスレータ関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallTranslator
helpviewer_keywords:
- SQLInstallTranslator function [ODBC]
ms.assetid: 453b21ff-3c2b-4069-8ff7-5c727f062d89
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b094aa730fff6db80b9addb63a92bee0f5f85b2a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300322"
---
# <a name="sqlinstalltranslator-function"></a>SQLInstallTranslator 関数
**適合 性**  
 バージョン導入: ODBC 2.5、非推奨  
  
 **まとめ**  
 ODBC 3.0 では **、SQL インストールトランスレータ**が[SQL インストールトランスレータに](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)置き換えられました。 SQL**インストールトランスレータ**への呼び出しは **、SQL インストールトランスレータEx**にマップされます。 詳細については **、「SQL インストールトランスレータ」を**参照してください。  
  
 アプリケーションが ODBC *3.x*ドライバー マネージャーで呼び出す場合 **、SQLInstallTranslator**は *、引数 lpszInfFile*が NULL 以外の値に設定されている場合は FALSE を返します。 ODBC *2.x*で使用される Odbc.inf ファイルは、下位互換性を維持するためにも ODBC *3.x*ではサポートされなくなりました。
