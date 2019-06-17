---
title: SQLInstallTranslator 関数 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de493cc42980390fee94ca4d86efc8f5cd40646c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63242312"
---
# <a name="sqlinstalltranslator-function"></a>SQLInstallTranslator 関数
**準拠**  
 バージョンが導入されました。ODBC 2.5、非推奨とされます。  
  
 **まとめ**  
 ODBC 3.0 で**SQLInstallTranslator**置き換わりました[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)します。 呼び出す**SQLInstallTranslator**にマップされる**SQLInstallTranslatorEx**します。 詳細については、次を参照してください。 **SQLInstallTranslatorEx**します。  
  
 **SQLInstallTranslator**アプリケーションが ODBC 3 で呼び出す場合は FALSE を返します *.x*ドライバー マネージャーで、 *lpszInfFile*引数が NULL 以外の値に設定します。 ODBC 2 で使用される Odbc.inf ファイル。*x* ODBC 3 ではサポートされなく *.x*旧バージョンとの互換性のためであっても、します。
