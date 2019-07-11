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
ms.openlocfilehash: 08a9e3a1afef8b9ea3bf1f4266196341e0edeb76
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792862"
---
# <a name="sqlinstalltranslator-function"></a>SQLInstallTranslator 関数
**準拠**  
 バージョンが導入されました。ODBC 2.5、非推奨とされます。  
  
 **概要**  
 ODBC 3.0 で**SQLInstallTranslator**置き換わりました[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)します。 呼び出す**SQLInstallTranslator**にマップされる**SQLInstallTranslatorEx**します。 詳細については、次を参照してください。 **SQLInstallTranslatorEx**します。  
  
 **SQLInstallTranslator**アプリケーションは、ODBC で呼び出す場合は FALSE を返します*3.x*ドライバー マネージャーで、 *lpszInfFile*引数が NULL 以外の値に設定します。 ODBC で使用される Odbc.inf ファイル*2.x* ODBC ではサポートされなく*3.x*旧バージョンとの互換性のためであっても、します。
