---
title: データソースを選択してください |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptwizard.selectdatasource.f1
ms.assetid: cdd84ad8-7c6a-41ac-bf51-1b0973434829
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6dab6158ba2d0854868bf60f2a73efce594b2cc9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66101440"
---
# <a name="select-the-data-source"></a>データ ソースを選択します
  レポート ウィザードのこのページでは、レポートのデータ ソースを定義できます。  
  
## <a name="options"></a>オプション  
 **共有データソース**  
 使用するデータ ソース接続情報が既に指定されている、定義済みの共有データ ソースを使用する場合に、 **[共有データ ソース]** を選択します。 一覧に、プロジェクトに含まれているすべての共有データ ソースが表示されます。  
  
 **新しいデータ ソース**  
 新しいデータ ソースを定義する場合は **[新しいデータ ソース]** を選択します。 データ ソースの情報は現在のレポートでのみ使用されます。  
  
 **名前**  
 データ ソースに対する接続の名前を入力します。 データ ソース名はレポート内で一意である必要があります。  
  
 **Type**  
 使用しているデータソースの種類を選択します (たとえば、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]データベースを使用している[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]場合は、を選択します)。  
  
 **接続文字列**  
 データ ソースの接続文字列を入力します。 接続文字列の詳細については、「 [Reporting Services のデータ接続、データソース、および接続文字列](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)」を参照してください。  
  
 
  **[編集]** をクリックし、 **[接続プロパティ]** ダイアログ ボックスを使用してデータ ソース サーバーを指定します。 ローカルまたはリモートのデータ ソースを指定できます。  
  
 
  **[資格情報]** をクリックして、データベースの資格情報を指定します。 少なくとも、レポートをデザインする目的でデータ ソースに接続するために、十分な資格情報を指定する必要があります。 レポートがレポート サーバーに置かれている場合、データベース資格情報を使用してレポートのすべてのユーザーに対応する必要があります。 たとえば、すべてのレポート ユーザーが各自の資格情報を使用してデータ ソースに接続するようにするには、 **[Windows 認証 (統合セキュリティ) を使用する]** を選択します。 指定する資格情報は、データ ソースで有効である必要があります。そのため、Windows 認証を選択する場合には、そのレポートを実行するすべてのユーザー アカウントによるデータ ソースへの接続が許可されることを確認してください。 データベース資格情報は、レポートとは別に管理できます。 詳細については、「 [レポートのデータ ソースの管理](report-data/manage-report-data-sources.md)」を参照してください。  
  
 **[共有データ ソースとして使用する]**  
 データ ソースをレポートではなく、共有データ ソースとしてプロジェクトに保存します。 こうすることで、そのデータ ソースをプロジェクト内の他のレポートにも使用できます。  
  
## <a name="see-also"></a>参照  
 [埋め込みデータ接続または共有データ接続またはデータソース &#40;レポートビルダーと SSRS&#41;](../../2014/reporting-services/embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)   
 [レポートデータソースの資格情報と接続情報を指定する](report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [レポートサーバーの Reporting Services](../../2014/reporting-services/reporting-services-report-server.md)   
 [RSReportDesigner 構成ファイル](report-server/rsreportdesigner-configuration-file.md)   
 [Reporting Services のデータ接続、データソース、および接続文字列](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [レポート ウィザードのヘルプ](../../2014/reporting-services/report-wizard-help.md)  
  
  
