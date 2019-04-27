---
title: プロジェクトを配置した後、パラメーター値を設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: c9dcca4d-f1a0-45ec-b078-f4d372589baf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f5e7248868a368ee0ea956b46b63c9c8d024393b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62766515"
---
# <a name="set-parameter-values-after-the-project-is-deployed"></a>プロジェクトを配置した後にパラメーターの値を設定する
  配置ウィザードを使用すると、プロジェクトをカタログに配置するときにサーバーの既定のパラメーター値を設定できます。 プロジェクトをカタログに配置した後、SQL Server Management Studio (SSMS) オブジェクト エクスプローラーまたは Transact-SQL を使用して、サーバーの既定値を設定できます。  
  
### <a name="to-set-server-defaults-with-ssms-object-explorer"></a>SSMS オブジェクト エクスプ ローラーを使用してサーバーの既定値を設定するには  
  
1.  **[Integration Services]** ノードでオブジェクトを選択して右クリックします。  
  
2.  **[プロパティ]** をクリックして、 **[プロジェクトのプロパティ]** ダイアログ ウィンドウを開きます。  
  
3.  **[ページの選択]** の **[パラメーター]** をクリックして、パラメーター ページを開きます。  
  
4.  **[パラメーター]** の一覧で目的のパラメーターを選択します。 注:**[コンテナー]** 列を使用すると、プロジェクト パラメーターとパッケージパラメーターを区別できます。  
  
5.  **[値]** 列で、目的のサーバーの既定のパラメーター値を指定します。  
  
 Transact-SQL を使用してサーバーの既定値を設定するには、[catalog.set_object_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-set-object-parameter-value-ssisdb-database) ストアド プロシージャを使用します。 現在のサーバーの既定値を表示するには、[catalog.object_parameters &#40;SSISDB Database&#41;](/sql/integration-services/system-views/catalog-object-parameters-ssisdb-database) ビューをクエリします。 サーバーの既定値をクリアするには、[catalog.clear_object_parameter_value &#40;SSISDB Database&#41;](/sql/integration-services/system-stored-procedures/catalog-clear-object-parameter-value-ssisdb-database) ストアド プロシージャを使用します。  
  
## <a name="see-also"></a>関連項目  
 [Integration Services &#40;SSIS&#41;パラメーター](integration-services-ssis-package-and-project-parameters.md)  
  
  
