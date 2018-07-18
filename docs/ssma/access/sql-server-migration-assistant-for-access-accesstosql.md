---
title: SQL Server Migration Assistant for Access (AccessToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 08/14/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 40c1eb02-26b2-44ba-969d-6c430c61c281
caps.latest.revision: 22
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: 3ffc062101434178ba5739c553508202d6b73c6a
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38985604"
---
# <a name="sql-server-migration-assistant-for-access-accesstosql"></a>SQL Server Migration Assistant for Access (AccessToSQL)
[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) のアクセスは、移行するためのツールからデータベース[!INCLUDE[msCoName](../../includes/msconame_md.md)]2010年による 97 のバージョンにアクセス[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2005/ [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008/ [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012/ [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014/ [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2016/ [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Windows と Linux (プレビュー) で 2017/ [!INCLUDE[msCoName](../../includes/msconame_md.md)] Azure SQL DB します。 変換する Access データベース オブジェクトのアクセス用の SSMA[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベース オブジェクトにこれらのオブジェクトの読み込み[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL へのアクセスからデータを移行したり[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL。  
  
このドキュメントは、SSMA for Access を紹介し、Access データベースへの移行の手順について説明します[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または SQL Azure と移行後に発生する可能性がある問題に関する情報。  
  
## <a name="contents"></a>目次  
  
|セクション|説明|  
|-----------|---------------|  
|[SSMA for Access の新機能](http://msdn.microsoft.com/a24d3fc0-6911-4bfa-828a-197abf222e02)|SSMA リリースへの変更を一覧表示します。|  
|[SQL Server Migration Assistant for Access をインストールします。](http://msdn.microsoft.com/dd50eebd-75df-4e0d-8c4d-88b511aae4c7)|インストールして、ライセンスの SSMA、および最新バージョンへのリンクについて、手順、SSMA のインストールの前提条件の一覧を表示します。|  
|[SQL Server Migration Assistant for Access の概要&#40;AccessToSQL&#41;](../../ssma/access/getting-started-with-sql-server-migration-assistant-for-access-accesstosql.md)|SSMA とそのユーザー インターフェイスが導入されています。|  
|[Access データベースの移行の準備](http://msdn.microsoft.com/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)|変換を Access データベースを準備する方法について説明します[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]SQL Azure です。|  
|[SQL Server へのアクセス データベースの移行](http://msdn.microsoft.com/76a3abcf-2998-4712-9490-fe8d872c89ca)|変換プロセスと、プロセスの各手順に関する詳細情報の概要を示します。|  
|[SQL Server への Access アプリケーションのリンク](http://msdn.microsoft.com/82374ad2-7737-4164-a489-13261ba393d4)|既存の Access アプリケーションを使用する方法について説明します[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]します。|  
|[ユーザー インターフェイス リファレンス](http://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)|SSMA のダイアログ ボックスのドキュメントが含まれています。|  
|[SSMA for Access コンソールの操作](http://msdn.microsoft.com/ef94e843-9f88-45a2-86c4-a0af268738c4)|SSMA コンソール アプリケーションでドキュメントが含まれて|  
|[SSMA の参考資料のアクセス](http://go.microsoft.com/fwlink/?LinkID=708538&clcid=0x409)|に関する追加情報についてを説明します。|  
  
