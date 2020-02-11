---
title: SQLInstallTranslator マッピング |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6433df796c88abd7873915266d1a2ca4041a5c62
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125725"
---
# <a name="sqlinstalltranslator-mapping"></a>SQLInstallTranslator のマッピング
ODBC *2.x アプリケーションが odbc* *3. x*ドライバーを使用して**sqlinstalltranslator**を呼び出すと、ドライバーマネージャーが呼び出しを**SQLInstallTranslatorEx**にマップします。アプリケーションでは、 *Lpszinffile*引数が NULL 以外の値に設定されている ODBC *3.x ドライバーマネージャー*で**sqlinstalltranslator**を呼び出すことはできません。 ODBC です。Odbc 2.x で使用される INF*ファイルは、* 旧バージョンとの互換性のため*に odbc 3.x*ではサポートされなくなりました。
