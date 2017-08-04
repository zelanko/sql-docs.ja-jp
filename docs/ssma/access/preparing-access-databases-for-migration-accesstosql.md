---
title: "Access データベース移行の準備 (AccessToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
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
caps.latest.revision: 20
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8319115ed2da6500644c89d513c1e44d3fb11825
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="preparing-access-databases-for-migration-accesstosql"></a>移行 (AccessToSQL) を Access データベースを準備します。
Access データベースを移行する前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、移行対象のデータベースを決定する必要があります、および、必ずこれらのデータベースが移行の準備ができています。  
  
## <a name="determining-when-to-migrate-to-sql-server"></a>SQL Server に移行する場合を判断します。  
アクセスするため、データベース エンジンとして使用される、Jet データベース エンジンとは、データ管理のための柔軟な使いやすいソリューションです。 ただし、データベース サイズが大きくなると複数のミッション クリティカル、多くのユーザーを検索に優れたパフォーマンス、セキュリティ、または可用性が必要です。 堅牢なデータ プラットフォームを必要とするアプリケーションでは、基になるデータベースにそれらのアプリケーションの移動を検討してください[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 移行するかを決めるの詳細については、次を参照してください。、[移行情報ページ](http://go.microsoft.com/fwlink/?LinkId=68571)上、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Web サイトです。  
  
データベースを移行した後に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]リンク テーブルを使用してアクセスを使用するを続けるか、アプリケーションを手動で移行することができます、[!INCLUDE[msCoName](../../includes/msconame_md.md)]と直接やり取りする .NET Framework ベースのコード[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
## <a name="determining-which-databases-to-migrate"></a>移行対象のデータベースを決定します。  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) のアクセスは、の Access データベースを見つけることができます。 それらのデータベースに関するメタデータをエクスポートすることができますし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 エクスポートおよびメタデータをクエリする方法の詳細については、次を参照してください。[アクセス インベントリをエクスポートする](http://msdn.microsoft.com/en-us/7e1941fb-3d14-4265-aff6-c77a4026d0ed)です。  
  
**注**でサポートされていないすべてのアクセス機能と設定、または、簡単に変換することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。 データベースの移行を開始する前に、次を参照してください。[互換性のないアクセス機能](http://msdn.microsoft.com/en-us/99d45b9c-e3b9-4d56-8c25-b594b887ace1)します。  
  
## <a name="preparing-for-migration"></a>移行の準備  
次のガイドラインを使用して、Access データベースへの移行のための準備を[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
### <a name="upgrading-older-access-databases"></a>古いアクセス データベースのアップグレード  
SSMA のアクセスは、Access 97 以降のバージョンをサポートします。 以前のバージョンの Access データベースがある場合は、開くし、Access 97 またはそれ以降のバージョンでデータベースを保存します。  
  
### <a name="removing-workgroup-protection"></a>ワークグループの保護の削除  
SSMA は、ワークグループの保護を使用するデータベースを移行できません。 Access データベースからワークグループ保護を削除するには、次を行うことができます。  
  
1.  Access データベース ファイルを別の場所にコピーします。  
  
2.  コピー先データベースを開きます。  
  
3.  **ツール**] メニューのをポイント**セキュリティ**、し、[**ユーザーとグループ権限**です。  
  
4.  選択、**ユーザー**オプションで、 **Admin**ユーザー、いることを確認し、 **Administer**アクセス許可が選択されています。  
  
5.  選択、**グループ**オプションで、**ユーザー**グループ化、およびいることを確認、 **Administer**アクセス許可が選択されています。  
  
6.  をクリックして**OK**、し、**ファイル**] メニューのをクリックして**終了**です。  
  
コピーしたデータベースを移行する SSMA を使えるようになりました。 スキーマの読み込み後[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]でデータベースを手動で保護することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
### <a name="backing-up-databases"></a>データベースのバックアップ  
データベースのアクセスを移行する前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、移行する場合、Access データベースをバックアップする必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]は移行先のデータベース オブジェクトとデータにアクセスします。  
  
Access データベースをバックアップする、**ツール**] メニューのをポイント**データベース ユーティリティ**、し、[**データベースのバックアップ**です。  
  
バックアップする方法については[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースを参照してください"Backing Up and Restoring Databases で[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]"で[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
### <a name="documenting-databases"></a>データベースを文書化します。  
データベース オブジェクト、ファイル サイズ、およびアクセス許可の一覧など、Access データベースのドキュメント プロパティに行うこともできます。 Access では、このドキュメントを生成する、**ツール**] メニューのをポイント**分析**、順にクリック**解析**です。  
  
## <a name="see-also"></a>参照  
[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
[SQL Server へのリンクの Access アプリケーション](http://msdn.microsoft.com/en-us/82374ad2-7737-4164-a489-13261ba393d4)  
  

