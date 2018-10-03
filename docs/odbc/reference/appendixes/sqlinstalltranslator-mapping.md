---
title: SQLInstallTranslator のマッピング |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 9760bfad769e9508d58d1cd00f98376dbd13d877
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47831388"
---
# <a name="sqlinstalltranslator-mapping"></a>SQLInstallTranslator のマッピング
ODBC 2 時にします。*x*アプリケーション呼び出し**SQLInstallTranslator**を通じて、ODBC 3 *.x*ドライバー、ドライバー マネージャーは、マップへの呼び出し**SQLInstallTranslatorEx**.アプリケーションは呼び出さないでください**SQLInstallTranslator** ODBC 3 *.x*ドライバー マネージャーで、 *lpszInfFile*引数が NULL 以外の値に設定します。 ODBC です。ODBC 2 で使用される INF ファイル。*x* ODBC 3 ではサポートされなく *.x*旧バージョンとの互換性のためであっても、します。
