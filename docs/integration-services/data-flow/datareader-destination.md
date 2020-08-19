---
description: DataReader 変換先
title: DataReader 変換先 | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.datareaderdest.f1
helpviewer_keywords:
- DataReader destination
- destinations [Integration Services], DataReader
ms.assetid: 56fcc4bf-c901-42c3-a71d-110039293431
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cf921ace25411ba18fc59310b0ad44f996ed2247
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88430894"
---
# <a name="datareader-destination"></a>DataReader 変換先

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  DataReader 変換先は、ADO.NET **DataReader** インターフェイスを使用して、データ フローのデータを公開します。 公開すると、そのデータを他のアプリケーションで使用できます。 たとえば、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポートのデータ ソースを構成して、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージの実行結果を使用できます。 構成するには、DataReader 変換先を実装するデータ フローを作成します。  
  
 プログラムで DataReader 変換先にアクセスして値を読み取る方法の詳細については、「 [ローカル パッケージの出力の読み込み](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)」をご覧ください。  
  
## <a name="configuration-of-the-datareader-destination"></a>DataReader 変換先の構成  
 DataReader 変換先のタイムアウト値を指定して、タイムアウトが発生した場合に変換先が失敗になるようにするかどうかを指定できます。 タイムアウトは、アプリケーションが指定した時間内にデータを要求しない場合に発生します。  
  
 DataReader 変換先は 1 つの入力をとります。 エラー出力はサポートされていません。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [Common Properties](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [DataReader 変換先のカスタム プロパティ](../../integration-services/data-flow/datareader-destination-custom-properties.md)  
  
 プロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
  
