---
title: "SQL Server 2012 SP2 リリース ノート | Microsoft Docs"
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: sql-non-specified
ms.technology: server-general
ms.custom: 
ms.date: 01/31/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67cb8b3e-3d82-47f4-840d-0f12a3bff565
caps.latest.revision: 
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 31f86cebfc5dc23aac8d56a1a9c75d140b744063
ms.sourcegitcommit: f0c5e37c138be5fb2cbb93e9f2ded307665b54ea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/27/2018
---
# <a name="sql-server-2012-sp2-release-notes"></a>SQL Server 2012 SP2 のリリース ノートします。
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]
このリリース ノートでは、SQL Server 2012 Service Pack 2 のインストールやトラブルシューティングを行う前に知っておく必要がある問題について説明しています。 リリース ノートはオンラインのみで入手でき、インストール メディアには含まれていません。 問題の検出に応じて、定期的に更新されます。 詳細については、「 [SQL Server 2012 Service Pack 2 で修正される問題](http://support.microsoft.com/KB/2958429) 」を参照してください。  
  
## <a name="choose-the-correct-file-to-download-and-install"></a>ダウンロードとインストールに使用する正しいファイルの選択  
次の表を使用して、現在インストールされているバージョンを基に、ダウンロードするファイルの場所と名前を確認します。 システム要件と基本的なインストール手順が含まれているページをダウンロードします。  
  
||||  
|-|-|-|  
|**現在インストールされているバージョン**|**目的**|**ダウンロードとインストール**|  
|32 ビット インストール:|||  
|SQL Server 2012 のいずれかのエディションの 32 ビット バージョン|SQL Server 2012 SP2 の 32 ビット バージョンにアップグレード|**SQLServer2012SP2-KB2958429-**<arch>**-**<lang id>**.exe** ( [SQL Server 2012 SP2 のダウンロード ページ](http://go.microsoft.com/fwlink/?LinkID=401006)|  
|SQL Server 2012 RTM Express の 32 ビット バージョン|SQL Server 2012 Express SP2 の 32 ビット バージョンにアップグレード|**SQLEXPR_**<arch>**_**<lang>**.msi** ( [SQL Server 2012 SP2 Express のダウンロード ページ](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|SQL Server 2012 のクライアントと管理ツールのみの 32 ビット バージョン (SQL Server 2012 Management Studio を含む)|SQL Server 2012 SP2 の 32 ビット バージョンにクライアントと管理ツールをアップグレード|**SQLEXPRWT_**<arch>**_**<lang>**.msi** ( [SQL Server 2012 SP2 Express のダウンロード ページ](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|SQL Server 2012 Management Studio Express の 32 ビット バージョン|SQL Server 2012 SP2 Management Studio Express の 32 ビット バージョンにアップグレード|**SQLManagementStudio_**<arch>**_**<lang>**.msi** ( [SQL Server 2012 SP2 Express のダウンロード ページ](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|SQL Server 2012 のいずれかのエディションの 32 ビット バージョンおよびクライアントと管理ツールの 32 ビット バージョン (SQL Server 2012 RTM Management Studio を含む)|SQL Server 2012 SP2 の 32 ビット バージョンにすべての製品をアップグレード|**SQLEXPRADV_**<arch>**_**<lang>**.msi** ( [SQL Server 2012 SP2 Express のダウンロード ページ](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|[Microsoft SQL Server 2012 RTM Feature Pack](http://www.microsoft.com/download/details.aspx?id=29065) または [Microsoft SQL Server 2012 SP1 Feature Pack](http://go.microsoft.com/fwlink/p/?LinkID=268266)の 1 つ以上のツールの 32 ビット バージョン|Microsoft SQL Server 2012 SP2 用 Feature Pack の 32 ビット バージョンにツールをアップグレード|Microsoft [SQL Server 2012 SP2 Feature Pack のダウンロード ページ](http://go.microsoft.com/fwlink/?LinkID=401008)の 1 つ以上のツール|  
|64 ビット インストール:|||  
|SQL Server 2012 のいずれかのエディションの 64 ビット バージョン|SQL Server 2012 SP2 の 64 ビット バージョンにアップグレード|SQLServer2012SP2-KB2958429-<arch>-<langid>.exe ( [SQL Server 2012 SP2 のダウンロード ページ](http://go.microsoft.com/fwlink/?LinkID=401006)から)|  
|SQL Server 2012 RTM Express の 64 ビット バージョン|SQL Server 2012 SP2 の 64 ビット バージョンにアップグレード|**SQLEXPR_**<arch>**_**<lang>**.msi** ( [SQL Server 2012 SP2 Express のダウンロード ページ](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|SQL Server 2012 のクライアントと管理ツールのみの 64 ビット バージョン (SQL Server 2012 Management Studio 含む)|SQL Server 2012 SP2 の 64 ビット バージョンにクライアントと管理ツールをアップグレード|**SQLEXPRWT_**<arch>**_**<lang>**.msi** ( [SQL Server 2012 SP2 Express のダウンロード ページ](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|SQL Server 2012 Management Studio Express の 64 ビット バージョン|SQL Server 2012 SP2 Management Studio Express の 64 ビット バージョンにアップグレード|**SQLManagementStudio_**<arch>**_**<lang>**.msi** ( [SQL Server 2012 SP2 Express のダウンロード ページ](http://go.microsoft.com/fwlink/?LinkID=401007)|  
|[Microsoft SQL Server 2012 RTM Feature Pack](http://www.microsoft.com/download/details.aspx?id=29065) または [Microsoft SQL Server 2012 SP1 Feature Pack](http://go.microsoft.com/fwlink/p/?LinkID=268266)の 1 つ以上のツールの 64 ビット バージョン|Microsoft SQL Server 2012 SP2 用 Feature Pack の 64 ビット バージョンにツールをアップグレード|Microsoft [SQL Server 2012 SP2 Feature Pack のダウンロード ページ](http://go.microsoft.com/fwlink/?LinkID=401008)の 1 つ以上のツール|  
  
