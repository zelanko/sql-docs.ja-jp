---
title: SQL Server Integration Services | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
keywords: SSIS
helpviewer_keywords:
- SSIS
- DTS [Integration Services]
- SQL Server Integration Services
- Integration Services
- DTS [Integration Services], about Integration Services
- data integration [Integration Services]
- Data Transformation Services
ms.assetid: c4398655-5657-4ae4-a690-a380790fe84f
caps.latest.revision: "51"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 812980a1fffc05c40531cb961502ec2b627fd402
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="sql-server-integration-services"></a>SQL Server Integration Services

 > 以前のバージョンの SQL Server に関連するコンテンツについては、「[SQL Server Integration Services](https://msdn.microsoft.com/library/ms141026(SQL.120).aspx)」をご覧ください。

[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] は、エンタープライズ レベルのデータ統合およびデータ変換ソリューションを構築するためのプラットフォームです。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] を使用すると、ファイルのコピーやダウンロード、イベントへの応答としての電子メール メッセージの送信、データ ウェアハウスの更新、データのクリーニングとマイニング、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のオブジェクトやデータの管理などにより、複雑なビジネスの問題を解決できます。 このパッケージは単独で使用することも、複雑なビジネス要件に対処するために他のパッケージと組み合わせて使用することもできます。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では、XML データ ファイル、フラット ファイル、リレーショナル データ ソースなど、さまざまなソースのデータを抽出および変換して、1 つ以上のターゲットに読み込むことができます。<br /><br /> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] には、組み込みのタスクと変換の豊富なセット、パッケージを作成するためのツール、およびパッケージの実行と管理のための [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスが含まれています。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のグラフィック ツールを使用すると、コードを 1 行も書かずにソリューションを作成することができます。また、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] の広範なオブジェクト モデルを使用して、パッケージをプログラムによって作成することもできます。この場合は、カスタム タスクや他のパッケージ オブジェクトを使用できます。

## <a name="try-sql-server-and-sql-server-integration-services"></a>SQL Server および SQL Server Integration Services をお試しください
- [![Evaluation Center からのダウンロード](../includes/media/download2.png)](http://go.microsoft.com/fwlink/?LinkID=829477) [SQL Server 2017 または 2016 のダウンロード](https://www.microsoft.com/evalcenter/evaluate-sql-server)
- [![Evaluation Center からダウンロードする](../includes/media/download2.png)](../ssdt/download-sql-server-data-tools-ssdt.md) [SQL Server Data Tools (SSDT) のダウンロード](../ssdt/download-sql-server-data-tools-ssdt.md)
- [![Evaluation Center からダウンロードする](../includes/media/download2.png)](../ssms/download-sql-server-management-studio-ssms.md) [SQL Server Management Studio (SSMS) のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)

##  <a name="infotipsql-servermediainfo-tippng-get-help"></a>![info_tip](../sql-server/media/info-tip.png) ヘルプの参照
 
- [SSIS の MSDN フォーラム - 質問する](https://social.msdn.microsoft.com/Forums/home?forum=sqlintegrationservices)
- [SSDT および SSMS の MSDN フォーラム - 質問する](https://social.msdn.microsoft.com/Forums/home?forum=sqltool)
- [Stack Overflow (タグ *ssis*) - 質問する](http://stackoverflow.com/questions/tagged/ssis)
- [Microsoft Connect - バグ報告と機能依頼](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit - SSIS に関する一般的なディスカッション](https://www.reddit.com/r/SQLServer/search?q=ssis&restrict_sr=on)
- [法人のお客様向けの Microsoft サポート オプション](https://support.microsoft.com/gp/support-options-for-business)
- [ビジネス ユーザー向けの Microsoft オプションに関するお問い合わせ先](https://support.microsoft.com/gp/contactus81?Audience=Commercial)
