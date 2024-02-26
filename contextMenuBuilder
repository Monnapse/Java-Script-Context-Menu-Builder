/*
    Made by Monnapse
*/

const addCssStyling = style => document.head.appendChild(document.createElement("style")).innerHTML=style;

const ContextMenuStyleTypes = {
    Default: {
        name: "default",
        css_styling: `
        /* CONTEXT MENU */
        .context-menu {
            position: fixed;
            visibility: hidden;
            z-index: 999;
            width: 200px;
            height: min-content;
            background-color: var(--dark-smoke);
            padding-top: 10px;
            padding-bottom: 10px;
            border-radius: 5px;
        }
        .context-menu button {
            width: 100%;
            height: 26px;
            text-align: left;
            vertical-align: middle;
            font-size: 14px;
            background-color: transparent;
            border: none;
            stroke: none;
            font-weight: 100;
        }
        .context-menu button:hover {
            background-color: var(--smoke-2);
        }
    `
    }
}

function ContextMenu() {
    /*
        Make a context menu
    */

    var self = {};
    var options = [];
    var currentStyleName = "";
    var currentStyleCss = "";
    var element = null;
    var showChecksFunction = null;
    var hideChecksFunction = null;
    
    /**
    * Create a new option inside the context menu.
    * @param {string} name Name for the option.
    * @param {string} text The text displayed for the option.
    * @param {function(event)} callback Callback function for when the option is selected/clicked.
    */
    self.newOption = function (name, text, callback) {
        options.push({
            name: name,
            text: text,
            callback: callback
        });
    }

    /**
    * This builds the context menu into elements.
    * @param {ContextMenuStyleTypes} style The style of the context menu (you can get premade styles from **ContextMenuStyleTypes** list).
    */
    self.buildContextMenu = function (style) {
        currentStyleName = style.name;
        currentStyleCss = style.css_styling;
        if (style.name=="default") {
            /*
                <div id="context-menu" class="context-menu">
                  <button id="context-menu-open">Open/Preview</button>
                  <button id="context-menu-download">Download</button>
                  <button id="context-menu-rename">Rename</button>
                  <button id="context-menu-delete">Delete</button>
                  <button id="context-menu-info">File Information</button>
                </div>
            */
            var contextMenuDiv = document.createElement("div");
            contextMenuDiv.classList.add("context-menu");
            contextMenuDiv.id = "context-menu";

            options.forEach(option => {
                var optionButton = document.createElement("button");
                optionButton.textContent = option.text;
                optionButton.addEventListener("click", option.callback);

                contextMenuDiv.appendChild(optionButton);
            });

            element = contextMenuDiv;
        }
    }

    /**
    * Displays the current context menu.
    * @param {number} left .
    * * @param {number} top .
    */
    self.showContextMenu = function (left, top) {
        if (element) {
            addCssStyling(currentStyleCss);
            document.body.insertBefore(element, document.body.firstChild);
            element.style.visibility = "visible";

            element.style.left = left + 'px';
            element.style.top = top + 'px';
        }
    }

    /**
    * Hides the context menu.
    */
    self.hideContextMenu = function () {
        if (element) {
            element.style.visibility = "hidden";
        }
    }

    /**
    * Add a function for when user requests context menu to check anything before displaying context menu.
    * Returning true = show context menu,
    * Returning false = not showing context menu,
    * Returning null = regular context menu.
    * @param {function} event The function to do the checks.
    */
    self.addShowChecksFunction = function(event) {showChecksFunction = event;}

    /**
    * Add a function for when user requests context menu to check anything before displaying context menu.
    * Returning true = hide context menu,
    * Returning anything else = nothing changes,
    * @param {function} event The function to do the checks.
    */
    self.addHideChecksFunction = function(event) {hideChecksFunction = event;}
    
    /**
    * Adds a contextmenu event listener for when the user requests context menu.
    */
    self.startShowFunctionality = function() {
        /*
            FUNCTIONALITY TASKS

            DEFAULT
        */
        document.addEventListener("contextmenu", event=>{
            var check = true;
            if (showChecksFunction) {
                check = showChecksFunction(event);
            }
            
            if (check) {
                event.preventDefault();
                self.showContextMenu(event.clientX, event.clientY);
            } else if (check == false) {
                event.preventDefault();
            }
        });
    }

    /**
    * Adds a click event listener for when the user is hiding context menu.
    */
    self.startHideFunctionality = function() {
        /*
            FUNCTIONALITY TASKS

            DEFAULT
        */
        document.addEventListener("click", event=>{
            var check = true;
            if (hideChecksFunction) {
                check = hideChecksFunction(event);
            }
            
            if (check) {
                event.preventDefault();
                self.showContextMenu(event.clientX, event.clientY);
            } else if (check == false) {
                event.preventDefault();
            }
        });
    }

    return self
}
