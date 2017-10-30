---
title: "レッスン 6: パラメーターを使用して、プロジェクト配置モデルと SSIS の |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 9216f18c-1762-4f2d-8c22-bd0ab7107555
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 547da852d6a52393be8e0adf53b4aa18955a6cad
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="lesson-6-using-parameters-with-the-project-deployment-model-in-ssis"></a>レッスン 6: SSIS でプロジェクト配置モデルを持つパラメーターを使用する
SQL Server 2012 では、Integration Services サーバーにプロジェクトを配置できる新しい配置モデルが導入されています。 Integration Services サーバーを使用すると、パッケージの管理、パッケージの実行、およびパッケージに合わせたランタイム値の構成を行うことができます。  
  
このレッスンでは、「 [レッスン 5: パッケージ配置モデルの SSIS パッケージ構成の追加](../integration-services/lesson-5-add-ssis-package-configurations-for-the-package-deployment-model.md) 」で作成したパッケージを変更して、パッケージ配置モデルを使用します。 構成値をパラメーターに置換して、サンプル データの場所を指定します。 または、チュートリアルに含まれている、レッスン 5 を完了した状態のパッケージをコピーすることもできます。  
  
Integration Services プロジェクト構成ウィザードを使用して、プロジェクトをプロジェクト配置モデルに変換し、構成値ではなくパラメーターを使用してディレクトリ プロパティを設定します。 このレッスンでは、新規プロジェクト配置モデルに既存の SSIS パッケージを変換するための手順について部分的に説明します。  
  
パッケージを再度実行すると、Integration Services サービスはパラメーターを使用して変数の値を生成します。さらに、この変数は Directory プロパティを更新します。 結果として、パッケージ構成ファイルで設定されたフォルダーではなく、パラメーター値によって指定された新しいデータ フォルダーのファイルに対してパッケージが繰り返し実行されます。  
  
> [!IMPORTANT]  
> このチュートリアルには、 **AdventureWorksDW2012** サンプル データベースが必要です。 **AdventureWorksDW2012**をインストールおよび配置する方法の詳細については、「 [SQL Server のサンプルとサンプル データベースのインストールに関する注意点](http://technet.microsoft.com/en-us/library/ms161556%28v=sql.105%29)」を参照してください。  
  
## <a name="lesson-tasks"></a>このレッスンの作業  
このレッスンの内容は次のとおりです。  
  
1.  [手順 1: レッスン 5 のパッケージのコピー](../integration-services/lesson-6-1-copying-the-lesson-5-package.md)  
  
2.  [手順 2: プロジェクトをプロジェクト配置モデルに変換する](../integration-services/lesson-6-2-converting-the-project-to-the-project-deployment-model.md)  
  
3.  [手順 3: レッスン 6 のパッケージのテスト](../integration-services/lesson-6-3-testing-the-lesson-6-package.md)  
  
4.  [手順 4: レッスン 6 のパッケージの展開](../integration-services/lesson-6-4-deploying-the-lesson-6-package.md)  
  
## <a name="start-the-lesson"></a>レッスンの開始  
[手順 1: レッスン 5 のパッケージのコピー](../integration-services/lesson-6-1-copying-the-lesson-5-package.md)  
  

