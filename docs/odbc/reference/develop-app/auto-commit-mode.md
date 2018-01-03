---
title: "自動コミット モード |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
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
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b2a9fd1565d0980e5af77d3cded499ce1f0091e5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="auto-commit-mode"></a>自動コミット モード
*自動コミット モードで*すべてデータベース操作は実行時にコミットされるトランザクション。 このモードは、1 つの SQL ステートメントで構成される多くの実際のトランザクションに適しています。 区切るか、これらのトランザクションの完了を指定する必要はありません。 トランザクションのサポートなしのデータベースでは、自動コミット モードは、唯一サポートされているモードです。 データベースではこのようなステートメントはコミットされると実行されるにロールバックする; 方法はありません。それらは常に自動コミット モードで。  
  
 基になる DBMS が自動コミット モードのトランザクションをサポートしていない場合、ドライバーをエミュレートできますそれらが実行されると、各 SQL ステートメントを手動でコミットしています。  
  
 SQL ステートメントのバッチが自動コミット モードで実行されるバッチ内のステートメントがコミットされたときに、データ ソース固有です。 コミットできるように、実行されるため、または、全体としてバッチ全体が実行された後です。 一部のデータ ソースは、これらの動作の両方をサポートする場合がありのいずれか、または、他のユーザーを選択する方法を提供する可能性があります。 具体的には、バッチの途中でエラーが発生した場合はデータ ソースの特定、既に実行されたステートメントがコミットまたはロールバックするかどうか。 したがって、バッチを使用し、コミットまたはロールバック全体として復元する必要があります相互運用可能なアプリケーションでは、手動コミット モードでのみバッチを実行する必要があります。
