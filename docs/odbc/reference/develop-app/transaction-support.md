---
title: トランザクションのサポート |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], degree of support
ms.assetid: d56e1458-8da2-4d73-a777-09e045c30a33
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: be133079c1b6beffd484942eb9ae058c14dd5c1f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63306034"
---
# <a name="transaction-support"></a>トランザクションのサポート
トランザクションのサポートの程度は、ドライバーの定義です。 ODBC は、そのデータを複数の更新プログラムを管理する必要がない、またはデスクトップでのシングル ユーザー データベースの実装に設計されています。 さらに、トランザクションをサポートする一部のデータベースのみに行うため SQL; のデータ操作言語 (DML) ステートメントトランザクションがアクティブな場合に、制限、またはデータ定義言語 (DDL) の使用に関する特別なトランザクション セマンティクスはあります。 つまり、テーブルに複数の同時更新プログラムの数と、トランザクション中にテーブルの定義の変更ではなく、トランザクションのサポートがあります。  
  
 アプリケーションが DDL トランザクション、およびトランザクションでは、DDL を呼び出すことによってなどの特別な効果に含まれるかどうか、トランザクションはサポートされているかどうかを決定**SQLGetInfo** SQL_TXN_CAPABLE オプションを使用します。 詳細については、次を参照してください。、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明。  
  
 ドライバーがトランザクションをサポートしていませんが、ロック、およびデータのロックを解除する (ODBC 以外の API を使用) 機能を備えて場合、アプリケーションは、ロックおよびロック解除のレコードと、必要に応じてテーブルでトランザクションのサポートを実現できます。 アカウント転送の例を実装するには、アプリケーションは両方のアカウントのレコードをロック、現在の値をコピー、借方最初のアカウント、2 つ目のアカウントのクレジットおよびレコードのロックを解除します。 すべての手順が失敗した場合、アプリケーションは、コピーを使用するアカウントにリセットされます。  
  
 トランザクションをサポートするものデータ ソースはできない、特定の環境内で一度に 1 つ以上のトランザクションをサポートすることがあります。 アプリケーション呼び出し**SQLGetInfo**データ ソースが同じ環境では、複数の接続で同時にアクティブなトランザクションをサポートできるかどうかを判断する SQL_MULTIPLE_ACTIVE_TXN オプションを使用します。 接続ごとに 1 つのトランザクションがあるため、これは、同じデータ ソースに複数の接続を持つアプリケーションに興味深いのみです。
