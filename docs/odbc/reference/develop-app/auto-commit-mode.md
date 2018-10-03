---
title: 自動コミット モード |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 87a5bababd2129ffb7e0aad36a2ceb3362d4acd9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792360"
---
# <a name="auto-commit-mode"></a>自動コミット モード
*自動コミット モードで*すべてのデータベース操作が実行時にコミットされたトランザクション。 このモードは、1 つの SQL ステートメントで構成される多くの実際のトランザクションに適しています。 場合によっては、区切るか、これらのトランザクションの完了を指定する必要はありません。 トランザクションをサポートしていないデータベースでは、自動コミット モードは、唯一サポートされているモードです。 このようなデータベースでは、ステートメントがコミットされたときが実行され、それらをロールバックして; する方法はありません。それらは常に自動コミット モードで。  
  
 基になる DBMS が自動コミット モードのトランザクションをサポートしていない場合、ドライバーをエミュレートできますそれらによって実行されるときに、各 SQL ステートメントを手動でコミットします。  
  
 SQL ステートメントのバッチが自動コミット モードで実行される、バッチ内のステートメントがコミットされた場合に、データ ソース固有です。 コミットできるように、実行されるため、または全体としてバッチ全体が実行された後です。 一部のデータ ソースは、これらの動作の両方をサポートする場合があり、他のユーザーまたは 1 つを選択する方法を提供する可能性があります。 具体的には、バッチの途中でエラーが発生した場合はデータ ソース固有の既に実行されたステートメントがコミットまたはロールバックするかどうか。 そのため、相互運用可能なアプリケーションを使用するバッチがコミットまたは全体がロールバックする必要があります手動コミット モードでのみ、バッチを実行する必要があります。
