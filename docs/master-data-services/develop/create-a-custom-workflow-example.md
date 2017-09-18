---
title: "カスタム ワークフローの例 (マスター データ サービス) | Microsoft Docs"
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
ms.assetid: dfd1616c-a75c-4f32-bdb1-7569e367bf41
caps.latest.revision: 6
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: bfc0c557f8c645fe7dfa56850bce64b533bc9340
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="create-a-custom-workflow---example"></a>カスタム ワークフローの作成 - 例
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] では、カスタム ワークフロー クラス ライブラリを作成するときに、Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender インターフェイスを実装するクラスを作成します。 このインターフェイスには、ワークフローの開始時に SQL Server MDS Workflow Integration Service によって呼び出される 1 つのメソッド (<xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A>) が含まれます。 <xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> メソッドには、2 つのパラメーターが含まれます。1 つは *workflowType* で、これには、[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] の **[ワークフローの種類]** ボックスに入力したテキストが含まれます。もう 1 つは *dataElement* で、これには、ワークフロー ビジネス ルールをトリガーしたアイテムのメタデータとアイテム データが含まれます。  
  
## <a name="custom-workflow-example"></a>カスタム ワークフローの例  
 次のコード例は、<xref:Microsoft.MasterDataServices.WorkflowTypeExtender.IWorkflowTypeExtender.StartWorkflow%2A> メソッドを実装して、ワークフロー ビジネス ルールをトリガーした要素の XML データから Name、Code、および LastChgUserName 属性を抽出する方法と、ストアド プロシージャを呼び出して、それらの属性を別のデータベースに挿入する方法を示しています。 アイテム データ XML の例と、それに含まれるタグの説明については、「[カスタム ワークフロー XML の説明 &#40;マスター データ サービス&#41;](../../master-data-services/develop/create-a-custom-workflow-xml-description.md)」を参照してください。  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Data.SqlClient;  
using System.Xml;  
  
using Microsoft.MasterDataServices.Core.Workflow;  
  
namespace MDSWorkflowTestLib  
{  
    public class WorkflowTester : IWorkflowTypeExtender  
    {  
        #region IWorkflowTypeExtender Members  
  
        public void StartWorkflow(string workflowType, System.Xml.XmlElement dataElement)  
        {  
            // Extract the attributes we want out of the element data.  
            XmlNode NameNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Name");  
            XmlNode CodeNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Code");  
            XmlNode EnteringUserNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/LastChgUserName");  
  
            // Open a connection on the workflow database.  
            SqlConnection workflowConn = new SqlConnection(@"Data Source=<Server instance>; Initial Catalog=WorkflowTest; Integrated Security=True");  
  
            // Create a command to call the stored procedure that adds a new user to the workflow database.  
            SqlCommand addCustomerCommand = new SqlCommand("AddNewCustomer", workflowConn);  
            addCustomerCommand.CommandType = System.Data.CommandType.StoredProcedure;  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Name", NameNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Code", CodeNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@EnteringUser", EnteringUserNode.InnerText));  
  
            // Execute the command.  
            workflowConn.Open();  
            addCustomerCommand.ExecuteNonQuery();  
            workflowConn.Close();  
        }  
  
        #endregion  
    }  
}  
```  
  
## <a name="see-also"></a>参照  
 [カスタム ワークフローの作成 &#40;マスター データ サービス&#41;](../../master-data-services/develop/create-a-custom-workflow-master-data-services.md)  
  
  
