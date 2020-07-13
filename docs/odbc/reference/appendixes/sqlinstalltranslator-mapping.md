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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8ab5ebccaac7ccf6374971c1d21040ad15fb3e55
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300584"
---
# <a name="sqlinstalltranslator-mapping"></a>SQLInstallTranslator のマッピング
ODBC *2.x アプリケーションが odbc* *3. x*ドライバーを使用して**sqlinstalltranslator**を呼び出すと、ドライバーマネージャーが呼び出しを**SQLInstallTranslatorEx**にマップします。アプリケーションでは、 *Lpszinffile*引数が NULL 以外の値に設定されている ODBC *3.x ドライバーマネージャー*で**sqlinstalltranslator**を呼び出すことはできません。 ODBC です。Odbc 2.x で使用される INF*ファイルは、* 旧バージョンとの互換性のため*に odbc 3.x*ではサポートされなくなりました。
