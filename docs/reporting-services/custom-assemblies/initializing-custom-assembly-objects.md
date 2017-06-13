---
title: "カスタム アセンブリ オブジェクトの初期化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
- initializing custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], initializing
- OnInit method
ms.assetid: 26fd74dc-d02f-40f7-aeb3-50ce05e9e6b9
caps.latest.revision: 36
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: dd3f6682e6297f86fbc4e67b98f5df48c7e94281
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="initializing-custom-assembly-objects"></a>カスタム アセンブリ オブジェクトの初期化
  状況によっては、カスタム アセンブリ クラスのプロパティ値とフィールド値をインスタンス化する際、これらを初期化する必要があります。 初期化が必要になる可能性が最も高いのは、レポートのグローバル オブジェクト コレクションからカスタム クラスと値を使用する場合です。 オーバーライドすることで、これを行う、 **OnInit**のメソッド、**コード**レポートのオブジェクト。 アクセスする**OnInit**を使用して、**コード**レポート定義の要素。 レポートで使用しようとするカスタム アセンブリのクラスのプロパティまたはフィールドの値を初期化するための 2 つの手法があります: を宣言し、使用して、クラスの新しいインスタンスを作成する**OnInit**を使用して、パブリックに使用可能なメソッドを呼び出すことができますか**OnInit**です。  
  
## <a name="global-object-collections-and-initialization"></a>グローバル オブジェクト コレクションと初期化  
 カスタム クラス変数を初期化するときは、 使用することができます、 **Globals**と**ユーザー**コレクション。 **パラメーター**、**フィールド**と**ReportItems**コレクション レポート ライフ サイクルの時点で不足しているときに、 **OnInit**メソッドが呼び出されます。 共有のコレクションを使用する**Globals**または**ユーザー**、含める必要があります、**レポート**オブジェクト参照。 たとえば、カスタム クラスを初期化するために、レポートにアクセスするユーザーの現在の言語を基づいて、**コード**要素は、次のようになります。  
  
```  
<Code>  
   Dim m_myClass As MyClass  
  
   Protected Overrides Sub OnInit()  
      m_myClass = new MyClass(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 前述のように、クラスのプロパティ値とフィールド値を初期化する 1 つの方法は、オーバーライドされたコンストラクターを呼び出すことによってクラスを宣言し、その新しいインスタンスを作成することです。  
  
 カスタム アセンブリのクラスのプロパティとフィールドの値を初期化するために別の方法がから定義をパブリックに使用可能なメソッドを呼び出すには、 **OnInit**メソッドです。 最初に、レポート定義ファイルのクラスのインスタンス名を追加する必要があります。 適切なアセンブリ参照とインスタンス名を追加した後は、初期化メソッドを呼び出して、クラスのプロパティ値とフィールド値を初期化できます。 **OnInit**メソッドは、次のようになります。  
  
```  
<Code>  
   Protected Overrides Sub OnInit()  
      m_myClass.MyInitializationMethod(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 カスタム クラスのアセンブリ参照とインスタンス名を追加する方法の詳細については、次を参照してください[レポート &#40; へのアセンブリ参照の追加。SSRS &#41;](../../reporting-services/report-design/add-an-assembly-reference-to-a-report-ssrs.md).  
  
 グローバル オブジェクト コレクションの詳細については、次を参照してください[式 &#40; 内で組み込みコレクション。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder.md).  
  
## <a name="see-also"></a>参照  
 [レポートでカスタム アセンブリの使用](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
