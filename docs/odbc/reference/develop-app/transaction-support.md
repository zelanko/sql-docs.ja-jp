---
title: トランザクションのサポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], degree of support
ms.assetid: d56e1458-8da2-4d73-a777-09e045c30a33
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b0e218f23ad720f8626c5b5e963038c194ae389
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="transaction-support"></a>トランザクションのサポート
トランザクションのサポートの度合いは、ドライバーの定義です。 ODBC は、そのデータに複数の更新を管理する必要がない、またはデスクトップでのシングル ユーザー データベースで実装するのには設計されています。 さらに、トランザクションをサポートする一部のデータベースのみに行うためです。 sql データ操作言語 (DML) ステートメント制限またはデータ定義言語 (DDL) の使用に関する特別なトランザクション セマンティクス、トランザクションがアクティブな場合です。 つまり、テーブルに複数の同時更新のではなく、トランザクション中にテーブルの定義と数を変更するトランザクションのサポートがあります。  
  
 アプリケーションが DDL は、トランザクション、およびを呼び出して、トランザクションでは、DDL をなどの特別な効果に含めることがあるかどうかのトランザクションはサポートされているかどうかを決定**SQLGetInfo** SQL_TXN_CAPABLE オプションを使用します。 詳細については、次を参照してください。、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明。  
  
 ドライバーがトランザクションをサポートしていませんが、機能を備えて (ODBC 以外の API を使用) をロックおよびデータのロックを解除する、アプリケーションは、ロックおよびロック解除のレコードとの必要に応じて、テーブルでトランザクションのサポートを実現できます。 アカウント転送の例を実装するには、アプリケーションは両方のアカウントのレコードをロック、現在の値をコピー、借方最初のアカウント、クレジットの 2 番目のアカウントでは、およびレコードのロックを解除します。 すべての手順に失敗した場合、アプリケーションは、コピーを使用するアカウントをリセットします。  
  
 トランザクションをサポートするものデータ ソースはできない、特定の環境で同時に複数のトランザクションをサポートすることがあります。 アプリケーションのコール**SQLGetInfo**データ ソースが同じ環境内で複数の接続で同時にアクティブなトランザクションをサポートできるかどうかを判断する SQL_MULTIPLE_ACTIVE_TXN オプションを使用します。 接続ごとに 1 つのトランザクションがあるため、これは、同じデータ ソースを複数の接続を持つアプリケーションに興味深いのみです。
