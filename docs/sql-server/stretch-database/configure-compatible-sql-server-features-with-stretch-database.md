---
title: "Stretch Database と互換性のある SQL Server 機能を構成する | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-stretch
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8121ede-1aec-459b-b7b0-1408bb3e62fb
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 84464c4553eab6d8e65c0bf6b476ae728e2a8463
ms.lasthandoff: 04/11/2017

---
# <a name="configure-compatible-sql-server-features-with-stretch-database"></a>Stretch Database と互換性のある SQL Server 機能を構成する
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

簡単な手順で、Stretch Database を操作できるように次の SQL Server 機能を構成します。
-   Always On
-   Always Encrypted
-   透過的なデータ暗号化 (TDE)
-   テンポラル テーブル

## <a name="configure-always-on-with-stretch-database"></a>Stretch Database で Always On を構成する
Stretch Database で Always On を使用している場合、データベース マスター キーがセカンダリ レプリカで使用できるようにする必要があります。 Stretch Database は、リモート Azure データベースへの接続に使用する資格情報をセキュリティで保護するために、データベース マスター キーを使用します。

Always On 可用性グループを設定したら、各セカンダリ レプリカでストアド プロシージャ **sp_control_dbmasterkey_password** を実行し、Stretch 対応データベースのパスワードを入力します。 詳細情報と例については、「 [sp_control_dbmasterkey_password](../../relational-databases/system-stored-procedures/sp-control-dbmasterkey-password-transact-sql.md)」を参照してください。 

## <a name="configure-always-encrypted-with-stretch-database"></a>Stretch Database で Always Encrypted を構成する
Always Encrypted と Stretch Database を併用するには、選択した列に対して暗号化を構成してから、テーブルで Stretch Database を有効にする必要があります。

テーブルで既に Stretch Database を有効にしており、Always Encrypted 列を使用する場合、次の手順を実行する必要があります。
1.   テーブルで Stretch Database を無効にして、リモート データを Azure から取得します。 詳細については、「 [Stretch Database を無効にして、リモート データを戻す](../../sql-server/stretch-database/disable-stretch-database-and-bring-back-remote-data.md)」を参照してください。
2.   選択した列で Always Encrypted を構成します。
3. テーブルに対する Stretch Database を再び有効にします。 詳細については、「 [Enable Stretch Database for a database](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md)」を参照してください。

## <a name="configure-transparent-data-encryption-tde-with-stretch-database"></a>Stretch Database で透過的なデータ暗号化 (TDE) を構成する

ローカル データベースで TDE が有効な場合、Stretch Database リモート エンドポイントでは自動的に有効になりません。 データベースで Stretch を有効にした後に、忘れずにリモート エンドポイントで TDE を有効にする必要があります。

## <a name="configure-temporal-tables-with-stretch-database"></a>Stretch Database でテンポラル テーブルを構成する
テンポラル テーブルを使用している場合、履歴テーブルで Stretch Database を有効にすることはできますが、現在のテーブルで有効にすることはできません。
-   Stretch Database でテンポラル テーブルを使用する方法のガイダンスについては、「 [システム バージョン管理されたテンポラル テーブルの履歴データの保有期間管理](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)」を参照してください。
-   スライディング ウィンドウを使用して履歴テーブルから移行する行をフィルターするには、「 [フィルター関数を使用して移行する行を選択する](../../sql-server/stretch-database/select-rows-to-migrate-by-using-a-filter-function-stretch-database.md)」を参照してください。
