---
title: 自動コミットモード |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81285112"
---
# <a name="auto-commit-mode"></a>自動コミット モード
*自動コミットモードでは、* すべてのデータベース操作は、実行時にコミットされるトランザクションです。 このモードは、1つの SQL ステートメントで構成される多くの実世界のトランザクションに適しています。 これらのトランザクションの完了を区切る必要はありません。 トランザクションをサポートしていないデータベースでサポートされるモードは、自動コミットモードのみです。 このようなデータベースでは、ステートメントは実行時にコミットされ、ロールバックすることはできません。このため、常に自動コミットモードになります。  
  
 基になる DBMS が自動コミットモードのトランザクションをサポートしていない場合、ドライバーは、実行時に各 SQL ステートメントを手動でコミットすることでエミュレートできます。  
  
 SQL ステートメントのバッチが自動コミットモードで実行される場合、バッチ内のステートメントがコミットされるときに、そのバッチはデータソース固有になります。 バッチ全体が実行された後、実行時または全体としてコミットできます。 データソースによっては、これらの動作の両方がサポートされている場合があります。また、どちらか一方を選択する方法が提供される場合もあります。 特に、バッチの途中でエラーが発生した場合、既に実行されているステートメントがコミットまたはロールバックされるかどうかは、データソースによって異なります。 そのため、バッチを使用して、それらを全体としてコミットまたはロールバックする必要がある相互運用可能なアプリケーションは、手動コミットモードでのみバッチを実行する必要があります。
