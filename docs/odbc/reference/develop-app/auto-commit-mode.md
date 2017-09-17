---
title: "自動コミット モード |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rolling back transactions [ODBC]
- auto-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: c8de5b60-d147-492d-b601-2eeae8511d00
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fb9b6d354657578f7188481a2e7ff7566f725c80
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="auto-commit-mode"></a>自動コミット モード
*自動コミット モードで*すべてデータベース操作は実行時にコミットされるトランザクション。 このモードは、1 つの SQL ステートメントで構成される多くの実際のトランザクションに適しています。 区切るか、これらのトランザクションの完了を指定する必要はありません。 トランザクションのサポートなしのデータベースでは、自動コミット モードは、唯一サポートされているモードです。 データベースではこのようなステートメントはコミットされると実行されるにロールバックする; 方法はありません。それらは常に自動コミット モードで。  
  
 基になる DBMS が自動コミット モードのトランザクションをサポートしていない場合、ドライバーをエミュレートできますそれらが実行されると、各 SQL ステートメントを手動でコミットしています。  
  
 SQL ステートメントのバッチが自動コミット モードで実行されるバッチ内のステートメントがコミットされたときに、データ ソース固有です。 コミットできるように、実行されるため、または、全体としてバッチ全体が実行された後です。 一部のデータ ソースは、これらの動作の両方をサポートする場合がありのいずれか、または、他のユーザーを選択する方法を提供する可能性があります。 具体的には、バッチの途中でエラーが発生した場合はデータ ソースの特定、既に実行されたステートメントがコミットまたはロールバックするかどうか。 したがって、バッチを使用し、コミットまたはロールバック全体として復元する必要があります相互運用可能なアプリケーションでは、手動コミット モードでのみバッチを実行する必要があります。
