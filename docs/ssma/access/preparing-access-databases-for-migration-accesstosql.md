---
title: Access データベースの移行の準備 (アクセス可能な Sql) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access databases, versions
- Access databases, when to migrate
- Access databases, workgroup security
- backing up databases
- documenting databases
- files, preparing
- migrating databases, versions
- migrating databases, when to migrate
- versions of Access
- workgroup security
ms.assetid: 9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: 58988d31687cacdce2954d8e4098d509a9dcbb2b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68260218"
---
# <a name="preparing-access-databases-for-migration-accesstosql"></a>移行のための Access データベースの準備 (アクセス可能な Sql)
Access データベースをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行する前に、移行するデータベースを決定し、それらのデータベースの移行準備ができていることを確認する必要があります。  
  
## <a name="determining-when-to-migrate-to-sql-server"></a>SQL Server に移行する場合の判断  
Access のデータベースエンジンとして使用される Jet データベースエンジンは、データ管理のための柔軟で使いやすいソリューションです。 ただし、データベースが大きくなり、ミッションクリティカルになるにつれて、多くのユーザーは、パフォーマンス、セキュリティ、または可用性の向上を必要としていることがわかります。 より堅牢なデータプラットフォームを必要とするアプリケーションでは、これらのアプリケーションの基に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]なるデータベースをに移動することを検討してください。 移行のタイミングを決定する方法の詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Web サイトの「[移行情報」ページ](https://go.microsoft.com/fwlink/?LinkId=68571)を参照してください。  
  
データベースをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行した後も、リンクテーブルを使用して引き続きアクセスできます。また、と[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]直接やり取りする .NET Framework ベースのコードにアプリケーションを手動で移行することもできます。  
  
## <a name="determining-which-databases-to-migrate"></a>移行するデータベースの決定  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Access の Migration Assistant (SSMA) は、Access データベースを見つけることができます。 その後、これらのデータベースに関するメタ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データをにエクスポートできます。 メタデータをエクスポートおよび照会する方法の詳細については、「[アクセスインベントリのエクスポート](exporting-an-access-inventory-accesstosql.md)」を参照してください。  

   > [!NOTE]
   > すべてのアクセス機能と設定がでサポートされているわけではあり[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ません。また、に簡単に変換することもできます。 データベースの移行を開始する前に、「互換性のない[アクセス機能](incompatible-access-features-accesstosql.md)」を参照してください。
  
## <a name="preparing-for-migration"></a>移行の準備  
への移行のために Access データベースを準備するには[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、次のガイドラインに従います。  
  
### <a name="upgrading-older-access-databases"></a>古い Access データベースのアップグレード  
SSMA for Access は、97以降のバージョンへのアクセスをサポートしています。 以前のバージョンの Access のデータベースを使用している場合は、Access 97 以降のバージョンでデータベースを開いて保存します。  
  
### <a name="removing-workgroup-protection"></a>ワークグループの保護の削除  
SSMA では、ワークグループ保護を使用するデータベースを移行することはできません。 Access データベースからワークグループ保護を削除するには、次の手順を実行します。  
  
1.  Access データベースファイルを別の場所にコピーします。  
  
2.  コピーしたデータベースを開きます。  
  
3.  [**ツール**] メニューの [**セキュリティ**] をポイントし、[**ユーザーとグループのアクセス許可**] を選択します。  
  
4.  [Users] \ (**ユーザー** \) オプションを選択し、**管理者**ユーザーを選択して、[**管理**] アクセス許可が選択されていることを確認します。  
  
5.  [**グループ**] オプションを選択し、[ **Users** ] グループを選択して、[**管理**] アクセス許可が選択されていることを確認します。  
  
6.  [ **OK**] をクリックし、[**ファイル**] メニューの [**終了**] をクリックします。  
  
これで、SSMA を使用して、コピーしたデータベースを移行できるようになりました。 スキーマをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]読み込んだ後、でデータベースを手動でセキュリティで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]保護することができます。  
  
### <a name="backing-up-databases"></a>データベースのバックアップ  
Access データベースをに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]移行する前に、移行する access データベースと、アクセスオブジェクトとデータを移行するデータベースの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]両方をバックアップする必要があります。  
  
Access データベースをバックアップするには、[**ツール**] メニューの [**データベースユーティリティ**] をポイントし、[**データベースのバックアップ**] を選択します。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースをバックアップする方法の詳細については、オンラインブックの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 「データベース[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のバックアップと復元」を参照してください。  
  
### <a name="documenting-databases"></a>データベースのドキュメント化  
また、Access データベースのデータベースオブジェクト、ファイルサイズ、アクセス許可の一覧などのプロパティを文書化することもできます。 Access でこのドキュメントを生成するには、[**ツール**] メニューの [**分析**] をポイントし、[**文書化**] をクリックします。  
  
## <a name="see-also"></a>参照  
[Access データベースの SQL Server への移行](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
[Access アプリケーションの SQL Server へのリンク](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md)
