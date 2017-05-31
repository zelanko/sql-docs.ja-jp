---
title: "カスタム レポート実行時の警告の抑制を解除する方法 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 0deed900-c910-4d12-aac0-6ab9e39eb068
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 20c37528ddb6bc1c93d86135ddcdf1ed0b9e2aa1
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="unsuppress-run-custom-report-warnings"></a>カスタム レポート実行時の警告の抑制を解除する方法
カスタム レポートについて表示される警告ダイアログ ボックスは 2 種類あります。 このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]を使用して、これらのボックスの表示抑制を解除する方法について説明します。  
  
既定で、 **[カスタム レポートの実行]** ダイアログ ボックスはカスタム レポートが実行される前に表示されます。 **[次回からこの警告を表示しない]** チェック ボックスをオンにすると、このダイアログ ボックスは表示されなくなります。 また、カスタム レポートを開き、リンクをクリックして別のカスタム レポートを開いたときにも、既定で **[カスタム レポートの実行]** ダイアログ ボックスが表示されます。 このダイアログ ボックスにはドリルスルー カスタム レポート ファイルへの完全パスが表示されます。 **[次回からこの警告を表示しない]** チェック ボックスをオンにすると、このダイアログ ボックスは表示されなくなります。  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio の使用  
  
#### <a name="to-unsuppress-the-main-custom-report-warning-dialog-box"></a>メインのカスタム レポート警告ダイアログ ボックスの抑制を解除するには  
  
1.  \<*Server*>\\<*Share*>|\<*Drive*>\Documents and Settings\\<UserProfile>\Application Data\Microsoft\Microsoft SQL Server\130\Tools\Shell\reports.xml に接続します。  
  
2.  **reports.xml**を右クリックし、 **[編集]**をクリックします。  
  
3.  **<SuppressWarning>true\<\/SuppressWarning> を <SuppressWarning>false\<\/SuppressWarning>** に変更します。  
  
4.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]を再起動します。  
  
#### <a name="to-unsuppress-the-drill-through-custom-report-warning-dialog-box"></a>ドリルスルー カスタム レポート警告ダイアログ ボックスの抑制を解除するには  
  
1.  \<*Server*>\\<*Share*>|\<*Drive*>\Documents and Settings\\<UserProfile>\Application Data\Microsoft\Microsoft SQL Server\130\Tools\Shell\reports.xml に接続します。  
  
2.  **reports.xml**を右クリックし、 **[編集]**をクリックします。  
  
3.  **<SuppressDrillthroughWarning>true\<\/SuppressDrillthroughWarning> を <SuppressDrillthroughWarning>false\<\/SuppressDrillthroughWarning >**に変更します。  
  
4.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)]を再起動します。  
  
## <a name="see-also"></a>参照  
[Management Studio におけるカスタム レポート](../../ssms/object/custom-reports-in-management-studio.md)  
[Management Studio へのカスタム レポートの追加](../../ssms/object/add-a-custom-report-to-management-studio.md)  
[カスタム レポートでのオブジェクト エクスプローラー ノード プロパティの使用](../../ssms/object/use-custom-reports-with-object-explorer-node-properties.md)  
  

