---
title: 'レッスン 5: レポート サーバーにレポート定義のパブリッシュ |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 57fab70f-4a72-4413-a0ad-d0525caca3f7
author: craigg-msft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 3430994f0c5cb2b4c09c47a4a8bebaa7da3eba3f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48163372"
---
# <a name="lesson-5-publish-the-report-definition-to-the-report-server"></a>レッスン 5 : レポート サーバーへのレポート定義のパブリッシュ
  レポート定義を更新する最後の作業として、レポート定義をレポート サーバーにパブリッシュします。  
  
### <a name="to-publish-the-report-to-the-report-catalog"></a>レポートをレポート カタログにパブリッシュするには  
  
1.  コードを置き換える、 `PublishReportDefinition()` 、Program.cs ファイル内のメソッド (Module1.vb [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) を次のコード。  
  
    ```csharp  
    private void PublishReportDefinition()  
    {  
        System.Console.WriteLine("Publishing Report Definition");  
  
        string reportPath =  
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012";  
  
        XmlSerializer serializer =  
            new XmlSerializer(typeof(Report));  
  
        using (MemoryStream stream = new MemoryStream())  
        {  
            // Serialize the report into the MemoryStream  
            serializer.Serialize(stream, _report);  
            stream.Position = 0;  
  
            byte[] bytes = stream.ToArray();  
  
            // Update the report on the report server  
            Warning[] warnings =   
                _reportService.SetItemDefinition(reportPath, bytes, null);  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub PublishReportDefinition()  
  
        System.Console.WriteLine("Publishing Report Definition")  
  
        Dim reportPath As String = _  
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012"  
        Dim serializer As XmlSerializer = _  
            New XmlSerializer(GetType(Report))  
  
        Using stream As MemoryStream = New MemoryStream  
  
            'Serialize the report into the MemoryStream  
            serializer.Serialize(stream, m_report)  
            stream.Position = 0  
  
            'Update the report on the report server  
            Dim bytes As Byte() = stream.ToArray  
            Dim warnings As Warning() = _  
                m_reportService.SetItemDefinition(reportPath, bytes, Nothing)  
  
        End Using  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a>次のレッスン  
 次のレッスンでは、コンパイルし、実行、`SampleRDLSchema`アプリケーション。 参照してください[レッスン 6: RDL スキーマ アプリケーションの実行&#40;VB C&#35;&#41;](../../2014/tutorials/lesson-6-run-the-rdl-schema-application-vb-csharp.md)します。  
  
## <a name="see-also"></a>参照  
 [RDL スキーマから生成されたクラスを使用してレポートを更新&#40;SSRS チュートリアル&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [レポート定義言語 &#40;SSRS&#41;](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
