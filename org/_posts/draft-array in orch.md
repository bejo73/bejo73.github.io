Använda arrayer i en orkestrering
För att använda sig av arrayer i en orkestrering så får man kapsla in det i ett objekt, XmlDocumentList i exemplet nedan.

using System;
using System.Collections.Generic;
using System.Text;
using System.Xml;
using System.Xml.XPath;

namespace My.Library
{
    [Serializable]
    public class XmlDocumentList
    {
        private List list = new List();

        public void Add(XmlDocument doc)
        {
            this.list.Add(doc);
        }

        public void Count()
        {
            return this.list.Count();
        }

    }
}

Läs mer på Richard Hallgrens blogg Gobbledygooks.
