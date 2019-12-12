# code-for-python
Ellaborative code on python
@@ -1 +1,2 @@
*.pyc
.idea
 5  .idea/encodings.xml 
@@ -0,0 +1,5 @@
<?xml version="1.0" encoding="UTF-8"?>
<project version="4">
  <component name="Encoding" useUTFGuessing="true" native2AsciiForPropertiesFiles="false" />
</project>

 9  .idea/json2csv.iml 
@@ -0,0 +1,9 @@
<?xml version="1.0" encoding="UTF-8"?>
<module type="PYTHON_MODULE" version="4">
  <component name="NewModuleRootManager">
    <content url="file://$MODULE_DIR$" />
    <orderEntry type="inheritedJdk" />
    <orderEntry type="sourceFolder" forTests="false" />
  </component>
</module>

 30  .idea/misc.xml 
@@ -0,0 +1,30 @@
<?xml version="1.0" encoding="UTF-8"?>
<project version="4">
  <component name="ProjectRootManager" version="2" project-jdk-name="Python 2.7.2 virtualenv at ~/.virtualenvs/salesboard" project-jdk-type="Python SDK" />
  <component name="PyConsoleOptionsProvider">
    <option name="myPythonConsoleState">
      <PyConsoleSettings />
    </option>
    <option name="myDjangoConsoleState">
      <PyConsoleSettings />
    </option>
  </component>
  <component name="SvnConfiguration" maxAnnotateRevisions="500" myUseAcceleration="nothing" myAutoUpdateAfterCommit="false" cleanupOnStartRun="false" SSL_PROTOCOLS="sslv3">
    <option name="USER" value="" />
    <option name="PASSWORD" value="" />
    <option name="mySSHConnectionTimeout" value="30000" />
    <option name="mySSHReadTimeout" value="30000" />
    <option name="LAST_MERGED_REVISION" />
    <option name="MERGE_DRY_RUN" value="false" />
    <option name="MERGE_DIFF_USE_ANCESTRY" value="true" />
    <option name="UPDATE_LOCK_ON_DEMAND" value="false" />
    <option name="IGNORE_SPACES_IN_MERGE" value="false" />
    <option name="CHECK_NESTED_FOR_QUICK_MERGE" value="false" />
    <option name="IGNORE_SPACES_IN_ANNOTATE" value="true" />
    <option name="SHOW_MERGE_SOURCES_IN_ANNOTATE" value="true" />
    <option name="FORCE_UPDATE" value="false" />
    <option name="IGNORE_EXTERNALS" value="false" />
    <myIsUseDefaultProxy>false</myIsUseDefaultProxy>
  </component>
</project>

 9  .idea/modules.xml 
@@ -0,0 +1,9 @@
<?xml version="1.0" encoding="UTF-8"?>
<project version="4">
  <component name="ProjectModuleManager">
    <modules>
      <module fileurl="file://$PROJECT_DIR$/.idea/json2csv.iml" filepath="$PROJECT_DIR$/.idea/json2csv.iml" />
    </modules>
  </component>
</project>

 7  .idea/other.xml 
@@ -0,0 +1,7 @@
<?xml version="1.0" encoding="UTF-8"?>
<project version="4">
  <component name="PyDocumentationSettings">
    <option name="myDocStringFormat" value="Plain" />
  </component>
</project>

 5  .idea/scopes/scope_settings.xml 
@@ -0,0 +1,5 @@
<component name="DependencyValidationManager">
  <state>
    <option name="SKIP_IMPORT_STATEMENTS" value="false" />
  </state>
</component> 
 8  .idea/testrunner.xml 
@@ -0,0 +1,8 @@
<?xml version="1.0" encoding="UTF-8"?>
<project version="4">
  <component name="TestRunnerService">
    <option name="projectConfiguration" value="Nosetests" />
    <option name="PROJECT_TEST_RUNNER" value="Nosetests" />
  </component>
</project>

 7  .idea/vcs.xml 
@@ -0,0 +1,7 @@
<?xml version="1.0" encoding="UTF-8"?>
<project version="4">
  <component name="VcsDirectoryMappings">
    <mapping directory="$PROJECT_DIR$" vcs="Git" />
  </component>
</project>

 26  README.md 
@@ -12,10 +12,32 @@ A convert to extract nested JSON data to CSV files

Basic (convert from a JSON file to a CSV file in same path):

    python json2csv.py /path/to/json_file.json /path/to/key_map_file.json
    python json2csv.py /path/to/json_file.json /path/to/outline_file.json

Specify CSV file

    python json2csv.py /path/to/json_file.json /path/to/key_map_file.json -o /some/other/file.csv
    python json2csv.py /path/to/json_file.json /path/to/outline_file.json -o /some/other/file.csv


For this JSON file:

    {
      "nodes": [
        {"source": {"author": "Someone"}, "message": {"original": "Hey!", "Revised": "Hey yo!"}},
        {"source": {"author": "Another"}, "message": {"original": "Howdy!", "Revised": "Howdy partner!"}},
        {"source": {"author": "Me too"}, "message": {"original": "Yo!", "Revised": "Yo, 'sup?"}}
      ]
    }

Use this outline file:

    {
      "map": [
        ["author", "source.author"],
        ["message", "message.original"]
      ],
      "collection": "nodes"
    }



 4  fixtures/bare_data.csv 
@@ -0,0 +1,4 @@
author,message
Someone,Hey!
Another,Howdy!
Me too,Yo!
 5  fixtures/bare_data.json 
@@ -0,0 +1,5 @@
[
{"source": {"author": "Someone"}, "message": {"original": "Hey!", "Revised": "Hey yo!"}},
{"source": {"author": "Another"}, "message": {"original": "Howdy!", "Revised": "Howdy partner!"}},
{"source": {"author": "Me too"}, "message": {"original": "Yo!", "Revised": "Yo, 'sup?"}}
] 
 6  fixtures/bare_outline.json 
@@ -0,0 +1,6 @@
{
    "map": [
        ["author", "source.author"],
        ["message", "message.original"]
    ]
}
 4  fixtures/data.csv 
@@ -0,0 +1,4 @@
author,message
Someone,Hey!
Another,Howdy!
Me too,Yo!
 5  fixtures/data.json 
@@ -0,0 +1,5 @@
{"nodes": [
{"source": {"author": "Someone"}, "message": {"original": "Hey!", "Revised": "Hey yo!"}},
{"source": {"author": "Another"}, "message": {"original": "Howdy!", "Revised": "Howdy partner!"}},
{"source": {"author": "Me too"}, "message": {"original": "Yo!", "Revised": "Yo, 'sup?"}}
]} 
 7  fixtures/outline.json 
@@ -0,0 +1,7 @@
{
    "map": [
        ["author", "source.author"],
        ["message", "message.original"]
    ],
    "collection": "nodes"
}
 42  json2csv.py 
@@ -4,35 +4,45 @@
import json
import operator
import os
from collections import OrderedDict
import logging

logging.basicConfig(level=logging.DEBUG)


class Json2Csv(object):
    """Process a JSON object to a CSV file"""
    collection = None

    def __init__(self, key_map, collection=None):
    def __init__(self, outline):
        self.rows = []

        if (not type(key_map) is dict):
            raise ValueError('You must pass in a key_map dictionary')
        elif (len(key_map) < 1):
            raise ValueError('You must pass in a key_map with at least one value to extract')
        for header, key in key_map.items():
        if not type(outline) is dict:
            raise ValueError('You must pass in an outline for JSON2CSV to follow')
        elif 'map' not in outline or len(outline['map']) < 1:
            raise ValueError('You must specify at least one value for "map"')

        key_map = OrderedDict()
        for header, key in outline['map']:
            splits = key.split('.')
            splits = [int(s) if s.isdigit() else s for s in splits]
            key_map[header] = splits

        self.key_map = key_map
        self.collection = collection
        if 'collection' in outline:
            self.collection = outline['collection']

    def load(self, json_file):
        self.process_each(json.load(json_file))

    def process_each(self, data, collection=None):
    def process_each(self, data):
        """Process each item of a json-loaded dict
        """
        if (self.collection and data.has_key(self.collection)):
        if self.collection and self.collection in data:
            data = data[self.collection]

        for d in data:
            logging.info(d)
            self.rows.append(self.process_row(d))

    def process_row(self, item):
@@ -43,7 +53,7 @@ def process_row(self, item):
        for header, keys in self.key_map.items():
            try:
                row[header] = reduce(operator.getitem, keys, item)
            except KeyError:
            except (KeyError, TypeError):
                row[header] = None

        return row
@@ -58,18 +68,20 @@ def write_csv(self, filename='output.csv'):
            writer.writeheader()
            writer.writerows(self.rows)


class MultiLineJson2Csv(Json2Csv):
    def load(self, json_file):
        self.process_each(json_file)

    def process_each(self, data):
        "Load each line of an interable collection (ie. file)"
    def process_each(self, data, collection=None):
        """Load each line of an iterable collection (ie. file)"""
        for line in data:
            d = json.loads(line)
            if (self.collection and data.has_key(self.collection)):
            if self.collection in data:
                data = data[self.collection]
            self.rows.append(self.process_row(d))


def init_parser():
    import argparse
    parser = argparse.ArgumentParser(description="Converts JSON to CSV")
@@ -88,15 +100,15 @@ def init_parser():

    key_map = json.load(args.key_map)
    loader = None
    if (args.each_line):
    if args.each_line:
        loader = MultiLineJson2Csv(key_map)
    else:
        loader = Json2Csv(key_map)

    loader.load(args.json_file)

    outfile = args.output_csv
    if (outfile is None):
    if outfile is None:
        fileName, fileExtension = os.path.splitext(args.json_file.name)
        outfile = fileName + '.csv'

 61  tests.py 
@@ -2,21 +2,22 @@
import json
from json2csv import Json2Csv, MultiLineJson2Csv


class TestJson2Csv(unittest.TestCase):

    def test_init(self):
        key_map = {'some_header': 'some_key'}
        loader = Json2Csv(key_map)
        self.assertEquals(loader.key_map, key_map)
        outline = {'map': [['some_header', 'some_key']]}
        loader = Json2Csv(outline)
        self.assertIn('some_header', loader.key_map)

        self.assertRaises(ValueError, Json2Csv, None)

        self.assertRaises(ValueError, Json2Csv, {})

    def test_process_row(self):
        "Given a valid key-map and data, it should return a valid row"
        key_map = {'id': '_id', 'count': 'count'}
        loader = Json2Csv(key_map)
        """Given a valid key-map and data, it should return a valid row"""
        outline = {'map': [['id', '_id'], ['count', 'count']]}
        loader = Json2Csv(outline)
        test_data = json.loads('{"_id" : "Someone","count" : 1}')
        row = loader.process_row(test_data)

@@ -28,10 +29,12 @@ def test_process_row(self):
        self.assertEquals(row['count'], 1)

    def test_process_row_nested_data(self):
        "Ensure that nested keys (with . notation) are processed"
        key_map = {'author': 'source.author', 'message': 'message.original'}
        """Ensure that nested keys (with . notation) are processed"""
        key_map = {"map": [['author', 'source.author'], ['message', 'message.original']]}
        loader = Json2Csv(key_map)
        test_data = json.loads('{"source": {"author": "Someone"}, "message": {"original": "Hey!", "Revised": "Hey yo!"}}')
        test_data = json.loads(
            '{"source": {"author": "Someone"}, "message": {"original": "Hey!", "Revised": "Hey yo!"}}'
        )
        row = loader.process_row(test_data)

        self.assertIs(type(row), dict)
@@ -42,15 +45,15 @@ def test_process_row_nested_data(self):
        self.assertEquals(row['message'], 'Hey!')

    def test_process_row_array_index(self):
        "Ensure that aray indices are properly handled as part of the dot notation"
        """Ensure that array indices are properly handled as part of the dot notation"""
        pass

    def test_process_each(self):
        key_map = {'id': '_id', 'count': 'count'}
        loader = Json2Csv(key_map)
        outline = {'map': [['id', '_id'], ['count', 'count']], 'collection': 'result'}
        loader = Json2Csv(outline)

        test_data = json.loads('{"result":[{"_id" : "Someone","count" : 1}]}')
        loader.process_each(test_data, collection='result')
        loader.process_each(test_data)

        self.assertEquals(len(loader.rows), 1)
        row = loader.rows[0]
@@ -65,8 +68,8 @@ def test_process_each_optional_key(self):
        """Ensure a key that is not always present won't prevent data extraction
        Where the data is missing, None is returned
        """
        key_map = {'id': '_id', 'count': 'count'}
        loader = Json2Csv(key_map)
        outline = {'map': [['id', '_id'], ['count', 'count']]}
        loader = Json2Csv(outline)

        test_data = json.loads('[{"_id" : "Someone","count" : 1}, {"_id": "Another"}]')
        self.assertEquals(len(test_data), 2)
@@ -77,9 +80,31 @@ def test_process_each_optional_key(self):
        self.assertEquals(second_row['id'], 'Another')
        self.assertIsNone(second_row['count'])

    def test_load(self):
        pass
    def test_load_json(self):
        outline = {"map": [['author', 'source.author'], ['message', 'message.original']], "collection": "nodes"}
        loader = Json2Csv(outline)
        with open('fixtures/data.json') as f:
            loader.load(f)

        first_row = loader.rows[0]
        self.assertEqual(first_row['author'], 'Someone')
        second_row = loader.rows[1]
        self.assertEqual(second_row['author'], 'Another')
        third_row = loader.rows[2]
        self.assertEqual(third_row['author'], 'Me too')

    def test_load_bare_json(self):
        outline = {"map": [['author', 'source.author'], ['message', 'message.original']]}
        loader = Json2Csv(outline)
        with open('fixtures/bare_data.json') as f:
            loader.load(f)

        first_row = loader.rows[0]
        self.assertEqual(first_row['author'], 'Someone')
        second_row = loader.rows[1]
        self.assertEqual(second_row['author'], 'Another')
        third_row = loader.rows[2]
        self.assertEqual(third_row['author'], 'Me too')

    def test_write_csv(self):
        pass
