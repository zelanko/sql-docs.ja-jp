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
ms.openlocfilehash: 50bfa00f482110d3d0695ef249e8758b5db02c80
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792810"
---
# <a name="sqlinstalltranslator-mapping"></a>SQLInstallTranslator のマッピング
ときに、ODBC *2.x*アプリケーション呼び出し**SQLInstallTranslator** ODBC を通じて*3.x*ドライバー、ドライバー マネージャーは、マップへの呼び出し**SQLInstallTranslatorEx**します。アプリケーションは呼び出さないでください**SQLInstallTranslator** ODBC で*3.x*ドライバー マネージャーで、 *lpszInfFile*引数が NULL 以外の値に設定します。 ODBC です。ODBC で使用される INF ファイル*2.x* ODBC ではサポートされなく*3.x*旧バージョンとの互換性のためであっても、します。
