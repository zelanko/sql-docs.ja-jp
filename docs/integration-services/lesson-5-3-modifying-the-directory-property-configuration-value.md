---
title: '手順 3 : Directory プロパティの構成値の変更 | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: tutorial
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: ba2a091f-361c-4331-afe2-53b465164c36
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0489101f98bcb4815e0c42e61763c894e61aeb00
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="lesson-5-3---modifying-the-directory-property-configuration-value"></a>レッスン 5-3 - Directory プロパティの構成値の変更
ここでは、SSISTutorial.dtsConfig ファイルに保存されている構成設定のうち、パッケージ レベル変数 `User::varFolderName`の Value プロパティを変更します。 この変数は、ForEach ループ コンテナーの Directory プロパティを更新します。 変更後の値は、前の実習で作成した **New Sample Data** フォルダーを参照するようにします。 構成設定を変更し、パッケージを実行すると、パッケージ レベル変数によって Directory プロパティが更新されます。この更新では、パッケージにもともと構成されていた Directory 値は使用されず、構成ファイルから生成された値が使用されます。  
  
### <a name="to-modify-the-configuration-setting-of-the-directory-property"></a>Directory プロパティの構成設定を変更するには  
  
1.  前の実習でパッケージ構成ウィザードを使用して作成した SSISTutorial.dtsConfig 構成ファイルを探し、メモ帳などのテキスト エディターで開きます。  
  
2.  前の実習で作成した **New Sample Data** フォルダーのパスに合わせて、 **ConfiguredValue** 要素の値を変更します。 パスは引用符で囲まないでください。 **New Sample Data** フォルダーがドライブのルート レベルにある場合 (C:\\)、更新された XML は次の例のようになります。  
  
    `<?xml version="1.0"?><DTSConfiguration><DTSConfigurationHeading><DTSConfigurationFileInfo GeneratedBy="DOMAIN\UserName" GeneratedFromPackageName="Lesson 5" GeneratedFromPackageID="{F4475E73-59E3-478F-8EB2-B10AFA61D3FA}" GeneratedDate="6/10/2012 8:16:50 AM"/></DTSConfigurationHeading><Configuration ConfiguredType="Property" Path="\Package.Variables[User::varFolderName].Properties[Value]" ValueType="String"><ConfiguredValue></ConfiguredValue></Configuration></DTSConfiguration>`  
  
    当然ながら、見出しの情報 **GeneratedBy**、 **GeneratedFromPackageID**、および **GeneratedDate** は、実際のファイルでは異なるものとなります。 **Configuration** 要素に注目してください。 変数の **Value** プロパティである `User::varFolderName`に、C:\New Sample Data が含まれています。  
  
3.  変更を保存し、テキスト エディターを閉じます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[手順 4:レッスン 5 のチュートリアル パッケージのテスト](../integration-services/lesson-5-4-testing-the-lesson-5-tutorial-package.md)  
  
  
  
