---
title: "カスタム ワークフロー XML の説明 (Master Data Services) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
ms.assetid: e267e5f4-38bb-466d-82e8-871eabeec07e
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ca6f208bab4ed0b7932d3bd5f7e9a911b8b2c8af
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-custom-workflow---xml-description"></a>カスタム ワークフローの XML の説明を作成します。
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] では、ワークフローの開始時に、SQL Server MDS Workflow Integration Service によって <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> メソッドが呼び出されます。 このメソッドは、ワークフロー ビジネス ルールをトリガーしたアイテムに関するメタデータとデータを、XML のブロックとして受け取ります。 たとえば、ワークフロー ハンドラーを実装するコードを参照してください[カスタム ワークフローの例 & #40 です。マスター データ サービス &#41;](../../master-data-services/develop/create-a-custom-workflow-example.md).  
  
 次の例は、ワークフロー ハンドラーに送られる XML の内容を示したものです。  
  
```scr  
<ExternalAction>  
  <Type>TEST</Type>  
  <SendData>1</SendData>  
  <Server_URL>This is my test!</Server_URL>  
  <Action_ID>Test Workflow</Action_ID>  
  <Model_ID>5</Model_ID>  
  <Model_Name>Customer</Model_Name>  
  <Entity_ID>34</Entity_ID>  
  <Entity_Name>Customer</Entity_Name>  
  <Version_ID>8</Version_ID>  
  <MemberType_ID>1</MemberType_ID>  
  <Member_ID>12</Member_ID>  
  <MemberData>  
    <ID>12</ID>  
    <Version_ID>8</Version_ID>  
    <ValidationStatus_ID>3</ValidationStatus_ID>  
    <ChangeTrackingMask>0</ChangeTrackingMask>  
    <EnterDTM>2011-02-25T20:16:36.650</EnterDTM>  
    <EnterUserID>2</EnterUserID>  
    <EnterUserName>MyUserName</EnterUserName>  
    <EnterUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</EnterUserMuid>  
    <EnterVersionId>8</EnterVersionId>  
    <EnterVersionName>VERSION_1</EnterVersionName>  
    <EnterVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</EnterVersionMuid>  
    <LastChgDTM>2011-02-25T20:16:36.650</LastChgDTM>  
    <LastChgUserID>2</LastChgUserID>  
    <LastChgUserName>MyUserName</LastChgUserName>  
    <LastChgUserMuid>EEF91D48-B673-4D83-B95F-5A363C11DE91</LastChgUserMuid>  
    <LastChgVersionId>8</LastChgVersionId>  
    <LastChgVersionName>VERSION_1</LastChgVersionName>  
    <LastChgVersionMuid>52B788C2-2750-4651-9DB0-2CB05A88AA5A</LastChgVersionMuid>  
    <Name>Test Customer</Name>  
    <Code>TC</Code>  
  </MemberData>  
</ExternalAction>  
```  
  
 次の表に、この XML に含まれるタグの一部を示します。  
  
|タグ|Description|  
|---------|-----------------|  
|\<型 >|入力したテキスト、**ワークフロー型**テキスト ボックスに[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]を読み込むには、どのカスタム ワークフロー アセンブリを識別します。|  
|\<SendData >|によって制御されるブール値、**メンバー データをメッセージに含める**の checkbox[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]です。 1 の値は、つまり、 \<MemberData > セクションは、それ以外の送信、 \<MemberData > セクションは送信されません。|  
|< Server_URL >|入力したテキスト、**ワークフロー サイト**テキスト ボックスに[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]です。|  
|< Action_ID >|入力したテキスト、**ワークフロー名**テキスト ボックスに[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]です。|  
|\<MemberData >|ワークフロー アクションをトリガーしたメンバーのデータが含まれます。 これは、含まれる場合にのみの値\<SendData > は 1 です。|  
|\<入力*xxx*>|このタグ セットには、メンバーの作成に関するメタデータ (作成日時や作成者など) が含まれます。|  
|\<LastChg*xxx*>|このタグ セットには、メンバーへの最終変更に関するメタデータ (変更日時や変更者など) が含まれます。|  
|\<名 >|変更されたメンバーの最初の属性。 この例のメンバーには、Name 属性と Code 属性のみが含まれています。|  
|\<コード >|変更されたメンバーの次の属性。 この例のメンバーにさらに多くの属性が含まれていた場合、それらはこのタグの後に続きます。|  
  
## <a name="see-also"></a>参照  
 [カスタム ワークフロー &#40; を作成します。マスター データ サービス &#41;](../../master-data-services/develop/create-a-custom-workflow-master-data-services.md)   
 [カスタム ワークフローの例 & #40 です。マスター データ サービス &#41;](../../master-data-services/develop/create-a-custom-workflow-example.md)  
  
  
