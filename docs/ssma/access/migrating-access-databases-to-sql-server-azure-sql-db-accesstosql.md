---
title: "SQL Server - Azure SQL DB への Access データベースの移行 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssma-access
ms.custom: 
ms.date: 08/15/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- instructions, migration
- migrating databases, overview
- overview, migration process
- procedure, migration
- recommended migration process
ms.assetid: 76a3abcf-2998-4712-9490-fe8d872c89ca
caps.latest.revision: "23"
author: Shamikg
ms.author: Shamikg
manager: murato
ms.workload: On Demand
ms.openlocfilehash: 31578b2e8eb59a357a33de0ebdcacbefefc895e0
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="migrating-access-databases-to-sql-server---azure-sql-db-accesstosql"></a>SQL Server - Azure SQL DB (AccessToSQL) へのアクセス データベースの移行
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) は短時間に Access データベースを移行するのに役立つ包括的な環境を提供するツール[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。 SSMA を使用すると、アクセスを確認することができ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure データベース オブジェクト、Access データベースの移行の評価、データベース オブジェクトに変換、読み込みに[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure、し、データを移行します。  
  
## <a name="recommended-migration-process"></a>推奨される移行プロセス  
正常に移行するオブジェクトとデータへのアクセスを[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure、次のプロセスを使用します。  
  
1.  [新しい SSMA プロジェクトを作成](http://msdn.microsoft.com/f2d1f0b0-5394-4adb-b3f3-abd71eb68ca7)です。 プロジェクトを作成することができます[プロジェクト オプションを設定](http://msdn.microsoft.com/0a7304df-2f35-4453-96ef-7ac83dea1167)(換算オプションの設定、移行オプション、およびデータ型のマッピングなど)。  
  
2.  [Access データベース ファイルを追加](http://msdn.microsoft.com/e944c740-4c8a-4bc1-b0ed-be57bc06dced)をプロジェクトにします。  
  
    コンピューターまたはネットワーク上にあるファイルを含む、個別のファイルを追加することができます。  
  
3.  [SQL Server のターゲット インスタンスに接続する](http://msdn.microsoft.com/f84cf007-ddf1-4396-a07c-3e0729abc769)または[SQL Azure のターゲット インスタンスに接続する](http://msdn.microsoft.com/1ba0d113-dc05-4431-8689-e14a8821bafd)です。  
  
    SQL Server または SQL Azure に接続できます。  
  
4.  1 つまたは複数の Access データベースの間のマッピングをカスタマイズして[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure スキーマ[マップ ソースとターゲット データベース](http://msdn.microsoft.com/69bee937-7b2c-49ee-8866-7518c683fad4)です。  
  
5.  ことができます必要に応じて、[評価レポートを作成する](http://msdn.microsoft.com/8b9e23d6-da62-437a-8c05-8ad2628b9441)に Access データベース オブジェクトを正常に変換するかどうかを決定する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure です。  
  
6.  [データベース オブジェクトを変換](http://msdn.microsoft.com/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure オブジェクトの定義。  
  
7.  [SQL Server に変換後のデータベース オブジェクトを読み込む](http://msdn.microsoft.com/4e854eee-b10c-4f0b-9d9e-d92416e6f2ba)します。  
  
    データベース オブジェクトを読み込むことができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SSMA、またはを使用して SQL Azure に保存したり[!INCLUDE[tsql](../../includes/tsql_md.md)]スクリプト。  
  
8.  [SQL Server にデータへのアクセスを移行](http://msdn.microsoft.com/f3b18af7-1af0-499d-a00d-a0af94895625)です。  
  
    > [!NOTE]  
    > 変換し、読み込むには、スキーマと 1 つの手順でデータを移行できます。 1 回のクリックの移行を実行する をクリックして、**変換、読み込み、および移行**ボタンをクリックします。  
  
9. ユーザー アクセス アプリケーション内のデータを使用するかどうか[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure を使用して[SQL Server テーブルにアクセス テーブルをリンク](http://msdn.microsoft.com/82374ad2-7737-4164-a489-13261ba393d4)です。  
  
またにこのプロセスを指示するのに、移行ウィザードを使用することができます。 詳細については、次を参照してください。[移行ウィザード](http://msdn.microsoft.com/5bab5914-b2ae-4795-8cf5-83e42d64bef2)です。  
  
## <a name="see-also"></a>参照  
[SQL Server Migration Assistant for Access の概要](http://msdn.microsoft.com/462a731f-08f1-44e1-9eeb-4deac6d2f6c5)  
[Access データベースの移行の準備](http://msdn.microsoft.com/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)
