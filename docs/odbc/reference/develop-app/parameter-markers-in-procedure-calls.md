---
title: プロシージャ呼び出しのパラメーター マーカー |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- parameter markers [ODBC]
- interoperability of SQL statements [ODBC], parameter markers
ms.assetid: cda56f2b-6eec-4cbc-8dbb-36d8fa9f9216
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 00aa87461c1b4a82fbedc7bd7faf1da6ff327265
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199148"
---
# <a name="parameter-markers-in-procedure-calls"></a>プロシージャ呼び出しのパラメーター マーカー
パラメーターを受け取るプロシージャを呼び出すときに、相互運用可能なアプリケーションは、リテラル パラメーター値の代わりにパラメーター マーカーを使用する必要があります。 一部のデータ ソースでは、プロシージャの呼び出しでのパラメーターをリテラル値の使用の使用はサポートされません。 パラメーターの詳細については、次を参照してください。[ステートメント パラメーター](../../../odbc/reference/develop-app/statement-parameters.md)します。 プロシージャの呼び出しの詳細については、次を参照してください。[プロシージャ呼び出し](../../../odbc/reference/develop-app/procedure-calls.md)、このセクションで後述します。
