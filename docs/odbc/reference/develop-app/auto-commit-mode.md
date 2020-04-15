---
title: 自動コミットモード |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- auto-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: c8de5b60-d147-492d-b601-2eeae8511d00
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6f19053eec7a48eba7a51425b01744f3acd10015
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285112"
---
# <a name="auto-commit-mode"></a>自動コミット モード
*自動コミット モードでは、* すべてのデータベース操作は、実行時にコミットされるトランザクションです。 このモードは、単一の SQL ステートメントで構成される多くの実世界のトランザクションに適しています。 これらのトランザクションの完了を区切ったり指定したりする必要はありません。 トランザクションがサポートされていないデータベースでは、自動コミット モードのみがサポートされます。 このようなデータベースでは、ステートメントは実行されるときにコミットされ、ロールバックする方法はありません。したがって、これらは常に自動コミットモードになります。  
  
 基になる DBMS が自動コミット モード トランザクションをサポートしていない場合、ドライバーは、各 SQL ステートメントを実行時に手動でコミットすることによって、トランザクションをエミュレートできます。  
  
 SQL ステートメントのバッチが自動コミット モードで実行される場合、バッチ内のステートメントがコミットされるときに、データ ソース固有の処理になります。 これらは、実行時にコミットすることも、バッチ全体が実行された後に全体としてコミットすることもできます。 データ ソースによっては、これらの動作の両方をサポートしている場合があり、いずれかを選択する方法を提供する場合があります。 特に、バッチの途中でエラーが発生した場合、既に実行済みのステートメントがコミットされるかロールバックされるかは、データ ソース固有です。 したがって、バッチを使用し、それらを全体としてコミットまたはロールバックする必要がある相互運用可能なアプリケーションは、手動コミット モードでのみバッチを実行する必要があります。
