---
title: 'タスク 4: SQL Server Data Tools | を使用して SSIS プロジェクトを作成するMicrosoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 8603ea91-2ec4-40b6-8070-4f824332f5d3
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: bcf16dc7d63e6a4acca6c30871666d1ffe996192
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "78171721"
---
# <a name="task-4-creating-an-ssis-project-using-sql-server-data-tools"></a>タスク 4: SQL Server Data Tools を使用して SSIS プロジェクトを作成する
  このタスクでは、 **SQL Server Data Tools**を使用して、クレンジングを自動化し、仕入先データを照合することにより、SSIS プロジェクトを作成します。

1.  **SQL Server Data Tools**を起動します。 [スタート] をクリックし、[**すべてのプログラム**]、[ **Microsoft SQL Server 2012**] の順にポイントし、[ **SQL Server Data Tools**] をクリックします。

2.  **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

3.  [**インストールされたテンプレート**] ペインで [**ビジネスインテリジェンス**] を展開し、[ **Integration Services**] を選択します。

     ![Visual Studio - [新しいプロジェクト] ダイアログ ボックス](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-01.jpg "Visual Studio - [新しいプロジェクト] ダイアログ ボックス")

4.  **プロジェクトの種類の一覧**で [ **Integration Services プロジェクト**] を選択します。

5.  [**名前**] に「 **CleanseAndCurateSuppliers** 」と入力し、[ **OK]** をクリックします。

6.  **ソリューションエクスプローラー**ウィンドウで、 **.dtsx**を右クリックし、[**名前の変更**] を選択します。 **ソリューションエクスプローラー**ウィンドウが表示されない場合は、メニューバーの [**表示**] をクリックし、[**ソリューションエクスプローラー**] をクリックします。

     ![Package.dtsx - [名前の変更] メニュー](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-02.jpg "Package.dtsx - [名前の変更] メニュー")

7.  「 **.Dtsx** 」と入力し、 **enter**キーを押します。 **拡張子**が **.dtsx**のままであることを確認します。

## <a name="next-step"></a>次の手順
 [タスク 5: データ フロー タスクを追加する](task-5-adding-data-flow-task.md)


