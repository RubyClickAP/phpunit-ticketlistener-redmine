PHPUnit_TicketListener_Redmine
===============================

Closing and reopening Redmine issues via PHPUnit tests.

Inspired by Raphael Stolt's article [Closing and reopening GitHub issues via PHPUnit tests](http://raphaelstolt.blogspot.com/2010/01/closing-and-reopening-github-issues-via.html). Read this article about how to use PHPUnit's ticket listeners.

Installation:
---------------------------------

    $pear channel-discovery pear.rpz.name
    $pear install rpz/PHPUnit_TicketListener_Redmine


Example configuration:
---------------------------------
    <phpunit>
	<listeners>
	    <listener class="PHPUnit_Extensions_TicketListener_Redmine" 
                 file="PHPUnit/Extensions/TicketListener/Redmine.php">
    		<arguments>
    		    <string>http://redmine.example.org</string><!-- redmine location -->
    		    <string>63d802d3d60069040f8fb0ea08b07d66</string><!-- your api-key for redmine -->
    		    <array>
        		<element key="0">
            		    <integer>5</integer><!-- redmine's id of issue's status 'closed', default 5 - closed -->
        		</element>
        		<element key="1">
            		    <integer>6</integer><!-- redmine's id of status that also closes issue (for example - canceled) -->
        		</element>
    		    </array>
    		    <array>
        		<element key="0">
            		    <integer>1</integer><!-- id of issue's status 'open' -->
        		</element>
        		<element key="1">
            		    <integer>2</integer><!-- id of issue's status 'open', default 2 - assigned -->
        		</element>
    		    </array>
    		    <integer>2</integer><!-- id of issue's status 'reopen', default 2 - assigned  -->
    		    <boolean>true</boolean><!-- print issue status changes  -->
    		</arguments>
	    </listener>
	</listeners>
    </phpunit>

Example usage:
---------------------------------
```php
class ExampleTest extends PHPUnit_Framework_TestCase {
    /**
     * @ticket 6666
     */
    public function testExampleMethod() {
        $this->assertTrue(true);
    }
}
```


    $phpunit --configuration phpunit-configuration.xml ExampleTest.php
    PHPUnit 3.5.2 by Sebastian Bergmann.

    Updating Redmine issue #6666, status: closed
    .

    Time: 0 seconds, Memory: 3.50Mb

    OK (1 test, 1 assertion)


    
