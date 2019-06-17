---
title: 手動コミット モード |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- manual-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: 9c4b3931-e48b-4960-89a2-5697537e9f51
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1952d4185c80a3b49b7742a9dba1f3d8d41a6ca6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62628913"
---
# <a name="manual-commit-mode"></a>手動コミット モード
*手動コミット モードで*アプリケーションを呼び出してトランザクションを完了する必要があります明示的に**SQLEndTran**にそれらをコミットまたはロールバックしています。 これは、ほとんどのリレーショナル データベースの通常のトランザクション モードです。  
  
 ODBC でのトランザクションは、明示的に開始する必要はありません。 代わりに、トランザクションは、データベースで動作しているアプリケーションを起動するたびに、暗黙的に開始します。 データ ソースの明示的なトランザクションの開始に使用する場合は、ドライバーはアプリケーションがトランザクションを必要とするステートメントを実行し、現在のトランザクションが存在しないときにそれを提供する必要があります。
