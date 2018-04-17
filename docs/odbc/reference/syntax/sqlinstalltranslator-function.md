---
title: SQLInstallTranslator 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cbd15cc8f2fc51d8d3c85269aad2854692ee966d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sqlinstalltranslator-function"></a>SQLInstallTranslator 関数
**準拠**  
 バージョンが導入されています。 ODBC 2.5、非推奨  
  
 **概要**  
 ODBC 3.0 **SQLInstallTranslator**代わりました[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)です。 呼び出す**SQLInstallTranslator**にマップされます**SQLInstallTranslatorEx**です。 詳細については、次を参照してください。 **SQLInstallTranslatorEx**です。  
  
 **SQLInstallTranslator**アプリケーションでは、それを呼び出す ODBC 3 の場合は FALSE を返します*.x*ドライバー マネージャーで、 *lpszInfFile*引数が NULL 以外の値に設定します。 ODBC 2 で使用される Odbc.inf ファイルです。*x* ODBC 3 ではサポートされなく*.x*旧バージョンとの互換性のためにあっても、します。
