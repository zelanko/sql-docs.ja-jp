---
title: "SQL Server Integration Services |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- SSIS
helpviewer_keywords:
- SSIS
- DTS [Integration Services]
- SQL Server Integration Services
- Integration Services
- DTS [Integration Services], about Integration Services
- data integration [Integration Services]
- Data Transformation Services
ms.assetid: c4398655-5657-4ae4-a690-a380790fe84f
caps.latest.revision: 51
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: e76675099ab290d29231d434eb74e92b613185b7
ms.openlocfilehash: 3c07bf1f605d23ffb4ffdd256ba446d215a046ab
ms.contentlocale: ja-jp
ms.lasthandoff: 09/29/2017

---
# <a name="sql-server-integration-services"></a>SQL Server Integration Services

 > SQL Server の以前のバージョンに関連するコンテンツでは、次を参照してください。 [SQL Server Integration Services](https://msdn.microsoft.com/en-US/library/ms141026(SQL.120).aspx)です。

[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] は、エンタープライズ レベルのデータ統合およびデータ変換ソリューションを構築するためのプラットフォームです。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] を使用すると、ファイルのコピーやダウンロード、イベントへの応答としての電子メール メッセージの送信、データ ウェアハウスの更新、データのクリーニングとマイニング、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のオブジェクトやデータの管理などにより、複雑なビジネスの問題を解決できます。 このパッケージは単独で使用することも、複雑なビジネス要件に対処するために他のパッケージと組み合わせて使用することもできます。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では、XML データ ファイル、フラット ファイル、リレーショナル データ ソースなど、さまざまなソースのデータを抽出および変換して、1 つ以上のターゲットに読み込むことができます。<br /><br /> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] には、組み込みのタスクと変換の豊富なセット、パッケージを作成するためのツール、およびパッケージの実行と管理のための [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] サービスが含まれています。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のグラフィック ツールを使用すると、コードを 1 行も書かずにソリューションを作成することができます。また、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] の広範なオブジェクト モデルを使用して、パッケージをプログラムによって作成することもできます。この場合は、カスタム タスクや他のパッケージ オブジェクトを使用できます。

## <a name="try-sql-server-and-sql-server-integration-services"></a>SQL Server と SQL Server Integration Services を実行してください。
- [![Evaluation Center からダウンロード](../includes/media/download2.png)](http://go.microsoft.com/fwlink/?LinkID=829477) [2017 または 2016、SQL Server のダウンロード](https://www.microsoft.com/evalcenter/evaluate-sql-server)
- [![Evaluation Center からダウンロードする](../includes/media/download2.png)](../ssdt/download-sql-server-data-tools-ssdt.md) [SQL Server Data Tools (SSDT) のダウンロード](../ssdt/download-sql-server-data-tools-ssdt.md)
- [![Evaluation Center からダウンロードする](../includes/media/download2.png)](../ssms/download-sql-server-management-studio-ssms.md) [SQL Server Management Studio (SSMS) のダウンロード](../ssms/download-sql-server-management-studio-ssms.md)

##  <a name="infotipsql-servermediainfo-tippng-get-help"></a>![info_tip](../sql-server/media/info-tip.png) ヘルプの参照
 
- [SSIS 用の MSDN フォーラムで質問します。](https://social.msdn.microsoft.com/Forums/en-us/home?forum=sqlintegrationservices)
- [SSDT と SSMS - MSDN フォーラムで質問します。](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltool)
- [スタックのオーバーフロー (タグ*ssis*)-質問](http://stackoverflow.com/questions/tagged/ssis)
- [Microsoft Connect - バグ報告と機能依頼](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit - 一般的な SSIS について](https://www.reddit.com/r/SQLServer/search?q=ssis&restrict_sr=on)
- [ビジネス ユーザー向けの Microsoft のサポート オプション](https://support.microsoft.com/gp/support-options-for-business)
- [ビジネス ユーザーの Microsoft のオプションにお問い合わせください。](https://support.microsoft.com/gp/contactus81?Audience=Commercial)

