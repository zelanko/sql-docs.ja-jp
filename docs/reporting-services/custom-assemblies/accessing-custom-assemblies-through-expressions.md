---
title: "式を介してカスタム アセンブリへのアクセス |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- expressions [Reporting Services], custom assemblies
- static member calls
- instance member calls [Reporting Services]
- calling class members
- custom assemblies [Reporting Services], expressions
ms.assetid: 917c4d47-1a95-4f54-98b1-e8cb2165d90f
caps.latest.revision: 32
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 70ff488827e5289d401bf62b67a82a08ecc25f70
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="accessing-custom-assemblies-through-expressions"></a>式を使用したカスタム アセンブリへのアクセス
  カスタム アセンブリを作成し、レポート デザイナーまたはレポート サーバーで利用可能にします。そして、適切なセキュリティ ポリシーを追加し、レポート定義のカスタム アセンブリへの参照を追加すると、レポートの式を使用してアセンブリ内のクラスのメンバーにアクセスできます。 式の中でカスタム コードを参照するには、アセンブリ内のクラスのメンバーを呼び出す必要があります。 呼び出す方法は、メソッドが静的であるかインスタンス ベースであるかにより異なります。  
  
## <a name="calling-static-members-from-a-report-definition-file"></a>レポート定義ファイルから静的メンバーを呼び出す  
 静的メンバーはクラスまたは型そのものに所属し、インスタンス化されたオブジェクトには所属しません。 静的メンバーはクラスから直接呼び出すことによりアクセスできます。 可能な場合は常に、静的メンバーを使用してレポートのカスタム関数を呼び出す必要があります。その理由は、静的メンバーがパフォーマンス上最も優れているからです。 静的メンバーを呼び出すには、形をとる式として参照する必要があります。 =*Namespace.Class.Method*です。  
  
#### <a name="to-call-static-members"></a>静的メンバーを呼び出すには  
  
-   静的メンバーを呼び出すには、式と、完全に修飾されたメンバー名とを等しくします。メンバー名を完全に修飾するには、名前空間、クラス名、およびメンバー名を使用します。 次の例では、 **ToGBP**に変換するメソッド、 **StandardCost**フィールドの値をドルから英ポンドに換算し、レポートの表示。  
  
    ```  
    =CurrencyConversion.DollarCurrencyConversion.ToGBP(Fields!StandardCost.Value)  
    ```  
  
### <a name="important-information-regarding-static-fields-and-properties"></a>静的フィールドおよび静的プロパティに関する重要な情報  
 現在のところ、すべてのレポートは同じアプリケーション ドメインで実行されます。 このことは、レポートのユーザー固有の静的データを、同じレポートの他のインスタンスから参照できることを意味します。 このような状況では、あるユーザーの静的データを、同時平行して個々のレポートを実行している他のすべてのユーザーが利用できる可能性があります。 このため、強くお勧め静的フィールドまたはカスタム アセンブリまたはプロパティを使用しないこと、**コード**要素です。 代わりに、レポートにインスタンス フィールドまたはプロパティを使用します。 しかし、静的メソッドは、状態やデータを保存しないため、使用可能です。  
  
## <a name="calling-instance-members-from-a-report-definition-file"></a>レポート定義ファイルからインスタンス メンバーを呼び出す  
 レポート定義内からアクセスする必要があるインスタンス メンバーがカスタム アセンブリ内に含まれている場合は、クラスのインスタンス名をレポートに追加する必要があります。 使用してクラスのインスタンス名を追加することができます、**コード**のタブ、**レポート プロパティ**ダイアログ。 クラスのインスタンスをレポートに追加する方法の詳細については、次を参照してください[カスタム コードやレポート デザイナー &#40; 内の式でのアセンブリ参照。SSRS &#41;](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).  
  
 静的メンバーを呼び出すには、形をとる式として参照する必要があります。 コードを =*です。InstanceName.Method*です。  
  
#### <a name="to-call-instance-members"></a>インスタンス メンバーを呼び出すには  
  
-   カスタム アセンブリのインスタンス メンバーを呼び出すには、参照する必要があります、**コード**キーワードの後にインスタンス名とメソッド。 次の例は、インスタンス メソッドを呼び出す**ToEUR**に変換する、 **StandardCost**フィールドの値をドルからユーロに換算し、レポートに表示します。  
  
    ```  
    =Code.m_myDollarCoversion.ToEUR(Fields!StandardCost.Value)  
    ```  
  
## <a name="see-also"></a>参照  
 [レポートでカスタム アセンブリの使用](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
