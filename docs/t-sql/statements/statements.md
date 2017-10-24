---
title: "ステートメント |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: d8d6f62a-e815-425c-a80e-a63fd34ec275
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d780aa463f6d4defe7dc727091863feabe7f338a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="transact-sql-statements"></a>Transact-SQL ステートメント
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-_md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

このリファレンス トピックには、TRANSACT-SQL (T-SQL) で使用するためのステートメントのカテゴリをまとめたものです。 左側のナビゲーションで表示されているステートメントのすべてを検索することができます。

## <a name="backup-and-restore"></a>バックアップと復元
Backup と restore ステートメントでは、バックアップを作成し、バックアップから復元する方法を提供します。  詳細については、次を参照してください。、[バックアップと復元の概要](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)です。

## <a name="data-definition-language"></a>データ定義言語
データ定義言語 (DDL) ステートメントでは、データ構造を定義します。 作成、変更、またはデータベースのデータ構造を削除するには、これらのステートメントを使用します。
- ALTER
- 照合順序
- CREATE
- DROP
- トリガーを無効にします。
- ENABLE TRIGGER
- 名前の変更
- 統計の更新

## <a name="data-manipulation-language"></a>データ操作言語
データ操作言語 (DML) では、データベースに格納されている情報に影響します。 挿入、更新、およびデータベース内の行を変更するには、これらのステートメントを使用します。

- BULK INSERT
- DELETE
- INSERT
- MERGE
- TRUNCATE TABLE

## <a name="permissions-statements"></a>権限ステートメント
権限ステートメントは、どのユーザーとログインできるデータにアクセスし、操作を実行を決定します。 認証とアクセスの詳細については、次を参照してください。、[セキュリティ センター](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)です。

## <a name="service-broker-statements"></a>Service Broker ステートメント
Service Broker は、メッセージング アプリケーションおよびキューイング アプリケーションのネイティブ サポートを提供する機能です。 詳細については、次を参照してください。 [Service Broker](../../relational-databases/service-broker/event-notifications.md)です。

## <a name="session-settings"></a>セッションの設定
SET ステートメントでは、現在のセッション ハンドルが時間の設定を実行する方法を指定します。 概要については、次を参照してください。 [SET ステートメント](set-statements-transact-sql.md)です。

